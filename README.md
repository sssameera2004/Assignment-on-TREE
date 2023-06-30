# Assignment-on-TREE
QUESTION 6:-

# Python program to find sum of all left leaves
 
# A Binary tree node
class Node:
    # Constructor to create a new Node
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None
 
# A utility function to check if a given node is leaf or not
def isLeaf(node):
    if node is None:
        return False
    if node.left is None and node.right is None:
        return True
    return False
 
# This function return sum of all left leaves in a
# given binary tree
def leftLeavesSum(root):
 
    # Initialize result
    res = 0
     
    # Update result if root is not None
    if root is not None:
 
        # If left of root is None, then add key of
        # left child
        if isLeaf(root.left):
            res += root.left.key
        else:
            # Else recur for left child of root
            res += leftLeavesSum(root.left)
 
        # Recur for right child of root and update res
        res += leftLeavesSum(root.right)
    return res
 
# Driver program to test above function
 
# Let us construct the Binary Tree shown in the above function
root = Node(20)
root.left = Node(9)
root.right = Node(49)
root.right.left = Node(23)       
root.right.right = Node(52)
root.right.right.left = Node(50)
root.left.left = Node(5)
root.left.right = Node(12)
root.left.right.right = Node(12)
print ("Sum of left leaves is", leftLeavesSum(root))

QUESTION 7:-
class Tree_structure:
   def __init__(self, data=None):
      self.key = data
      self.children = []

   def set_root(self, data):
      self.key = data

   def add_values(self, node):
      self.children.append(node)

   def search_val(self, key):
      if self.key == key:
         return self
      for child in self.children:
         temp = child.search(key)
         if temp is not None:
            return temp
      return None

   def summation_nodes(self):
      sum_val = self.key
      for child in self.children:
         sum_val = sum_val + child.summation_nodes()
      return sum_val

tree = None

print('Menu (no duplicate keys allowed)')
print('add <data> at root')
print('add <data> below <data>')
print('summation')
print('quit')

while True:
   my_input = input('What would you like to do? ').split()

   operation = my_input[0].strip().lower()
   if operation == 'add':
      data = int(my_input[1])
      newNode = Tree_structure(data)
      sub_op = my_input[2].strip().lower()
      if sub_op == 'at':
         tree = newNode
      elif sub_op == 'below':
         my_pos = my_input[3].strip().lower()
         key = int(my_pos)
         ref_node = None
         if tree is not None:
            ref_node = tree.search_val(key)
         if ref_node is None:
            print('No such key exists')
            continue
         ref_node.add_values(newNode)

   elif operation == 'summation':
      if tree is None:
         print('The tree is empty')
      else:
         summation_val = tree.summation_nodes()
         print('Sum of all the nodes is : {}'.format(summation_val))

   elif operation == 'quit':
      break

METHOD 2:-
class Node:  
    def __init__(self,data):  
        #Assign data to the new node, set left and right children to None  
        self.data = data;  
        self.left = None;  
        self.right = None;  
   
class SumOfNodes:  
    def __init__(self):  
        #Represent the root of binary tree  
        self.root = None;  
      
    #calculateSum() will calculate the sum of all the nodes present in the binary tree  
    def calculateSum(self, temp):  
        sum = sumRight = sumLeft = 0;  
          
        #Check whether tree is empty  
        if(self.root == None):  
            print("Tree is empty");  
            return 0;  
        else:  
            #Calculate the sum of nodes present in left subtree  
            if(temp.left != None):  
                sumLeft = self.calculateSum(temp.left);  
              
            #Calculate the sum of nodes present in right subtree  
            if(temp.right != None):  
                sumRight = self.calculateSum(temp.right);  
              
            #Calculate the sum of all nodes by adding sumLeft, sumRight and root node's data  
            sum = temp.data + sumLeft + sumRight;   
        return sum;  
   
bt = SumOfNodes();  
#Add nodes to the binary tree  
bt.root = Node(5);  
bt.root.left = Node(2);  
bt.root.right = Node(9);  
bt.root.left.left = Node(1);  
bt.root.right.left = Node(8);  
bt.root.right.right = Node(6);  
   
#Display the sum of all the nodes in the given binary tree  
print("Sum of all nodes of binary tree: " + str(bt.calculateSum(bt.root)));  

QUESTION 8:-
# Python3 implementation to count subtrees
# that Sum up to a given value x

# class to get a new node


class getNode:
	def __init__(self, data):

		# put in the data
		self.data = data
		self.left = self.right = None

# function to count subtrees that
# Sum up to a given value x


def countSubtreesWithSumX(root, count, x):

	# if tree is empty
	if (not root):
		return 0

	# Sum of nodes in the left subtree
	ls = countSubtreesWithSumX(root.left,
							count, x)

	# Sum of nodes in the right subtree
	rs = countSubtreesWithSumX(root.right,
							count, x)

	# Sum of nodes in the subtree
	# rooted with 'root.data'
	Sum = ls + rs + root.data

	# if true
	if (Sum == x):
		count[0] += 1

	# return subtree's nodes Sum
	return Sum

# utility function to count subtrees
# that Sum up to a given value x


def countSubtreesWithSumXUtil(root, x):

	# if tree is empty
	if (not root):
		return 0

	count = [0]

	# Sum of nodes in the left subtree
	ls = countSubtreesWithSumX(root.left,
							count, x)

	# Sum of nodes in the right subtree
	rs = countSubtreesWithSumX(root.right,
							count, x)

	# if tree's nodes Sum == x
	if ((ls + rs + root.data) == x):
		count[0] += 1

	# required count of subtrees
	return count[0]


# Driver Code
if __name__ == '__main__':

	# binary tree creation
	#		 5
	#		 / \
	#	 -10	 3
	#	 / \ / \
	#	 9 8 -4 7
	root = getNode(5)
	root.left = getNode(-10)
	root.right = getNode(3)
	root.left.left = getNode(9)
	root.left.right = getNode(8)
	root.right.left = getNode(-4)
	root.right.right = getNode(7)

	x = 7

	print("Count =",
		countSubtreesWithSumXUtil(root, x))

METHOD 2:-
import sys 
# A class to store a binary tree node
class Node:
    def __init__(self, data, left=None, right=None):
        self.data = data
        self.left = left
        self.right = right
 # The helper function to count all subtrees having the same value of nodes.
# The function returns the root node's value if all nodes in the subtree
# rooted at root have the same values; otherwise, it returns infinity
def countSubtrees(root, count=0):
 
    # base case: empty tree
    if root is None:
        return -sys.maxsize, count
 
    # if the root is a leaf node, increase the count and return root node data
    if root.left is None and root.right is None:
        count = count + 1
        return root.data, count
 
    # recur for the left and right subtree
    left, count = countSubtrees(root.left, count)
    right, count = countSubtrees(root.right, count)
 
    # 1. The left subtree is empty, and the right subtree data matches the root
    # 2. The right subtree is empty, and the left subtree data matches the root
    # 3. Both left and right subtrees are non-empty, and their data matches the root
 
    if ((left == -sys.maxsize and right == root.data) or
            (right == -sys.maxsize and left == root.data) or
            (left == right and left == root.data)):
        # increase the count and return root node data
        count = count + 1
        return root.data, count
 
    # return infinity if root's data doesn't match with left or right subtree
    return sys.maxsize, count
 
 
if __name__ == '__main__':
 
    ''' Construct the following tree
                 1
               /   \
              2     3
            /     /   \
           4     5     6
         /     /   \     \
        4     5     5     7
    '''
 
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.right.left = Node(5)
    root.right.right = Node(6)
    root.left.left.left = Node(4)
    root.right.left.left = Node(5)
    root.right.left.right = Node(5)
    root.right.right.right = Node(7)
 
    print(countSubtrees(root)[1])
 
QUESTION 9:-

import queue

class Node:
    def __init__(self, data):
        self.left = None
        self.data = data
        self.right = None

def max_level_sum(root):
    if root:
        q = queue.Queue()
        q.put(root)
        q.put(None)
        node = None
        level = max_level = current_sum = max_sum = 0
        while not q.empty():
            node = q.get()
            if node is None:
                if current_sum > max_sum:
                    max_sum = current_sum
                    max_level = level
                current_sum = 0
                if not q.empty():
                    level += 1
                    q.put(None)
            else:
                current_sum += node.data
                if node.left:
                    q.put(node.left)
                if node.right:
                    q.put(node.right)

        return max_level
    else:
        return None

root = Node(1)
root.left = Node(2)
root.right = Node(3)
root.left.left = Node(4)
root.left.right = Node(5)
root.right.left = Node(6)
root.right.right = Node(7)
print(max_level_sum(root))

Question 10:-

# Recursive Python3 program to print
# odd level nodes
 
# Utility method to create a node
class newNode:
    def __init__(self, data):
        self.data = data
        self.left = self.right = None
 
def printOddNodes(root, isOdd = True):
     
    # If empty tree
    if (root == None):
        return
 
    # If current node is of odd level
    if (isOdd):
        print(root.data, end = " ")
 
    # Recur for children with isOdd
    # switched.
    printOddNodes(root.left, not isOdd)
    printOddNodes(root.right, not isOdd)
 
# Driver code
if __name__ == '__main__':
    root = newNode(1)
    root.left = newNode(2)
    root.right = newNode(3)
    root.left.left = newNode(4)
    root.left.right = newNode(5)
    printOddNodes(root)




