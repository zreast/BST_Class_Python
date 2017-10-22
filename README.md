```
class Node:
    def __init__(self, username_in, password_in):
        self.username = username_in
        self.password = password_in
        self.left = None
        self.right = None


class BST:
    def __init__(self):
        self.root = None

    def insert(self, new_node):
        if (self.root is None):
            self.root = new_node
        else:
            self.insert_node(self.root, new_node)

    def insert_node(self, current_node, new_node):
        if (new_node.username <= current_node.username):
            if (current_node.left is not None):
                self.insert_node(current_node.left, new_node)
            else:
                current_node.left = new_node
        elif (new_node.username > current_node.username):
            if (current_node.right is not None):
                self.insert_node(current_node.right, new_node)
            else:
                current_node.right = new_node

    def find(self, username):
        return self.find_node(self.root, username)

    def find_node(self, current_node, username):
        if (current_node is None):
            return False
        elif (username == current_node.username):
            return current_node.password
        elif (username < current_node.username):
            return self.find_node(current_node.left, username)
        else:
            return self.find_node(current_node.right, username)
```

read “user_pass.txt” file contains username and password to create an order by username BST, using recursion to insert or find any node. 

About reading file in Python, can use either:

```
with open("user_pass.txt", "r") as f: 
    content = f.readlines()
```

or

```
file = open("user_pass.txt", "r")
for i in file:
    content.append(i)
```

‘content’ will become lists of each line
