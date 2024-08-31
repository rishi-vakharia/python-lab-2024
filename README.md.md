[TOC]

# Loops

## Problems

Q1. Check whether a number `num` is prime or not.

```
Test Case 1
Input:
4
Output:
Not Prime

Test Case 2
Input:
71
Output:
Prime
```



Q2. Implement x**y using a loop.

```
Test Case 1
Input:
3 4
Output:
81
Explanation:
3 raised to the power 4 is 81

Test Case 2
Input:
2 5
Output:
32
```



Q3. Find sum of all digits of a number `num`.

```
Test Case 1
Input:
881
Output:
17
Explanation:
881 -> 8 + 8 + 1 -> 17

Test Case 2
Input:
2345
Output:
14
```



Q4. Find `n!` using a loop.

```
Test Case 1
Input:
5
Output:
120
Explanation:
5 factorial is 120

Test Case 2
Input:
8
Output:
40320
```



Q5. Find the min and max value from a list using a loop.

```
Test Case 1
Input:
7, 3, 1, 8, 7, 5, 9
Output:
1
9
Explanation:
In the list [7, 3, 1, 8, 7, 5, 9], the min value is 1 and max value is 9.
```



Q6. Convert a number `num` from decimal format to binary format. Input can be an integer (decimal format). Output can be a string (binary format).

```
Test Case 1
Input:
19
Output:
10011
Explanation:
The binary representation of 19 is 10011.

Test Case 2
Input:
8
Output:
1000

Test Case 2
Input:
63
Output:
111111
```



Q7. Print the pattern below using loops.

```
    *
   ***
  *****
 *******
*********
```



## Hints

Q1

1. Number `n` is not a prime if some number can divide it (other than 1 and n ofc).
2. You only need to check from 2 to sqrt(n).



Q2

1. You need a **running product** here. Initialize a running product variable `p` to 1.
2. We need to do `p *= x` for `y` number of times.



Q3

1. Extract digits using `n%10`
2. Reduce the num using `num//=10`



Q4

1. You need a **running product** here. Initialize a running product variable `p` to 1.
2. We need to do `p *= i` where i goes from 1 to n.



Q5

1. Initialize `max` to a[0].
2. Update `max` whenever a[i] > max.



Q6

1. Find `num % 2`.
2. Keep doing `num //= 2`



Q7

1. Count empty space, stars, empty spaces for each line.

2. | row  | spaces | stars   | spaces |
   | ---- | ------ | ------- | ------ |
   | 1    | 4      | 1       | 4      |
   | 2    | 3      | 3       | 3      |
   | 3    | 2      | 5       | 2      |
   | 4    | 1      | 7       | 1      |
   | 5    | 0      | 9       | 0      |
   | i    | 5 - i  | 2*i - 1 | 5 - i  |

3. For each line, you can run 3 loops.
4. Use print("*", end = "") to avoid moving to the next line.



## Solutions

```python
# Q1. Check whether a number is prime or not.

from math import sqrt

# Return true if the num is prime and false otherwise
def is_prime(num):

    if(num <= 1):
        return False  # handle edge cases (primes start from 2)

    for i in range(2, int(sqrt(num)) + 1):
        if num % i == 0:
            return False  # not prime
    
    return True  # prime

# Taking input
num = int(input())

if(is_prime(num)):
    print("Prime")
else:
    print("Not Prime")
```



```python
# Q2. Implement x**y using a loop.

# Return x raised to power y
def power(x, y):
    p = 1
    for i in range(y):
        p *= x
    return p

# Taking input
str1 = input()

x, y = str1.split(" ")

x = int(x)
y = int(y)

print(power(x, y))
```



```python
# Q3. Find sum of all digits of a number.

# Return the sum of digits in a number
def sum_of_digits(num):

    sum = 0  # Start with sum 0

    while(num > 0):
        digit = num%10  # Extract the last digit
        sum += digit  # Keep track of sum of digits
        num //= 10  # Drop the last digit
    
    return sum


# Taking input
num = int(input())

print(sum_of_digits(num))
```



```python
# Q4. Find n! using a loop.

# Return the factorial of number n
def factorial(n):
    p = 1
    for i in range(1, n+1):
        p *= i
    return p


# Taking input
n = int(input())

print(factorial(n))
```



```python
# Q5. Find the min and max value of a list using a loop.

# Taking input
str1 = input()
a = [int(x) for x in str1.split(", ")]  # This is how you can take a list as input in a single line
n = len(a)  # num of elements in list a

# Initialize min
min_val = a[0]

# Find min
for i in range(0, n):
    if(a[i] < min_val):
        min_val = a[i]

print(min_val)

# Initialize max
max_val = a[0]

# Find max
for i in range(0, n):
    if(a[i] > max_val):
        max_val = a[i]

print(max_val)
```



```python
# Q6. Convert a number from decimal format to binary format. Input can be an integer (decimal format). Output can be a string (binary format).

# Returns the binary representation of num
def decimal_to_binary(num):

    if num == 0:
        return "0"  # Handle edge cases
    
    binary = ""

    while(num > 0):
        bin_digit = num % 2  # Extract a binary bit (0/1)
        binary = binary + str(bin_digit)  # Append the binary bit to our ans
        num //= 2

    return binary[::-1]  # Reverse the string to get the correct representation

# Taking input
num = int(input())

# Calling the decimal to binary function
print(decimal_to_binary(num))
```



```python
# Q7
# For each row 1 to 5
for i in range(1, 6):

    # Print spaces
    for j in range(0, 5-i):
        print(" ", end="")
    
    # Print stars
    for j in range(0, 2*i-1):
        print("*", end="")

    # Print spaces
    for j in range(0, 5-i):
        print(" ", end="")

    print() # new line after a row
```



# Dictionaries

## Problems

Q1. Make a grocery list using python dictionaries. It should keep track of item name, price (per kg) and quantity (in kg). The grocery list contains the following items:

| Item     | Price (Rs) |
| -------- | ---------- |
| Tomato   | 25.49      |
| Potato   | 30.25      |
| Carrot   | 70         |
| Cucumber | 30.29      |
| Apple    | 100.10     |
| Orange   | 40         |
| Banana   | 65         |

Initialize the data structure with item name and price as given in the above table and quantity as 0. The goal is to update the quantity of the appropriate item as the user adds items to his/her cart and compute the total bill amount. 

```
Test Case 1
Input: 
Tomato 2
Apple 1.5
Tomato 1

Output: 
Rs. 226.62 
Explanation: Total amount = (3 * 25.49) + (15 * 100.10) = 76.47 + 150.15 = 226.62
```



Q2. You will be given two Dictionaries (you can hardcode them in your code):

- `city_population`: A dictionary where keys are city names and values are the populations of those cities.
- `state_cities`: A dictionary where keys are state names and values are lists of cities in that state.

```python
city_population = {
    'Ahmadabad': 8650605,
    'Lucknow': 3945409,
    'Bangalore': 13607800,
    'Mangalore': 749073,
    'Varanasi': 1754425,
    'Chennai': 11776147,
    'Kochi': 3406055,
    'Nagpur': 3046687	
}

state_cities = {
    'Gujarat': ['Ahmadabad'],
    'Karnataka': ['Bangalore', 'Mangalore'],
    'Tamil Nadu': ['Chennai', 'Kochi'],
    'Uttar Pradesh': ['Lucknow', 'Varanasi'],
    'Maharashtra': ['Nagpur']
}
```

As an input to your program, you'll be given a State from the `state_cities` dictionary. You have to return the average population of a city in this state based on the data available to you in `city_population` dictionary and `state_cities` dictionary.

```
Test Case 1
Input:
Karnataka
Output:
7178436

Test Case 2
Input:
Maharashtra
Output:
3046687
```



Q3. Write a Python program to create a dictionary where the keys are numbers between 1 and 10 (both included) and the values are the squares of the keys.



## Hints

Q1

1. While taking user input, you can update (or initialize) the qty of item.
2. To compute the total, you just have to iterate through the dictionary and keep a **running sum** for the total.



Q2

1. Keep track of total population of a state using a **running sum** variable.
2. Find avg population = total population / num of cities.



Q3

1. No need of any hints here. :smiley:



## Solutions

```python
#   Q1
#   Vege/Fruit, Its Price (per kg), Its Qty (in kg)
cart = {
    "Tomato": { "Price": 25.49, "Qty": 0 },
    "Potato": { "Price": 30.25, "Qty": 0 },
    "Carrot": { "Price": 70, "Qty": 0 },
    "Cucumber": { "Price": 30.29, "Qty": 0 },
    "Apple": { "Price": 100.10, "Qty": 0 },
    "Orange": { "Price": 40, "Qty": 0 },
    "Banana": { "Price": 65, "Qty": 0 }
}


""" Taking the input """

while True:
    user_input = input()

    if user_input.strip() == "":   # stop when user input is empty
        break

    # Vege/Fruit, Its Qty
    item, qty = user_input.split(" ")
    qty = float(qty)

    if item not in cart:
        cart[item]["Qty"] = qty
    else:
        cart[item]["Qty"] += qty


""" Computing the total cost of cart """

total_amt = 0

for item in cart:
    cost = cart[item]["Price"] * cart[item]["Qty"]   # cost = price_per_kg * qty
    total_amt += cost


print(f'Rs. {total_amt:.2f}')
```



```python
# Q2
city_population = {
    'Ahmadabad': 8650605,
    'Lucknow': 3945409,
    'Bangalore': 13607800,
    'Mangalore': 749073,
    'Varanasi': 1754425,
    'Chennai': 11776147,
    'Kochi': 3406055,
    'Nagpur': 3046687	
}

state_cities = {
    'Gujarat': ['Ahmadabad'],
    'Karnataka': ['Bangalore', 'Mangalore'],
    'Tamil Nadu': ['Chennai', 'Kochi'],
    'Uttar Pradesh': ['Lucknow', 'Varanasi'],
    'Maharashtra': ['Nagpur']
}


""" Taking input """
state = input()

total_pop = 0  # Count the total population of this state based on given cities

for city in state_cities[state]:
    total_pop += city_population[city]

num_cities = len(state_cities[state])  # Num of cities in this state acc. to 'state_cities' dictionary

avg_pop = total_pop // num_cities  # Average population of a city in this state

print(avg_pop)
```



```python
# Q3
dict1 = {}

for i in range(1, 11):
    dict1[i] = i**2

print(dict1)
```



# Lists

## Problems

Q1. Given two integer lists as input, write a program to print the maximum and minimum values among all the elements in both lists.

```
Test Case 1
Input:
1, 3, 4, 5, 2, 6
3, 4, 8, 3, 10, 1
Output:
10
1
Explanation:
The maximum value is 10 from the second list.
The minimum value is 1 from the first/second list.
```



Q2. Write a program to compute the transpose of a matrix. The first two input values are the number of rows and columns, and the next list of input values represents the elements of the matrix.

```
Test Case 1
Input:
3
2
1, 2, 3, 4, 5, 6
Output:
[[1, 3, 5], [2, 4, 6]]
Explanation:
Input matrix is:
[[1, 2],
 [3, 4],
 [5, 6]]
Its Transpose will be:
[[1, 3, 5], 
 [2, 4, 6]]
```



Q3. Write a program to compute the multiplication of two matrices. The first input value will be the dimensions of the first matrix (rows and columns), followed by the elements of the first matrix. The second input value will be the dimensions of the second matrix (rows and columns), followed by the elements of the second matrix. Ensure that the number of columns in the first matrix matches the number of rows in the second matrix.

```
Test Case 1
Input:
2
3
1, 2, 3, 4, 5, 6
3
2
7, 8, 9, 10, 11, 12
Output:
[[58, 64], [139, 154]]
Explanation:
Input matrices are:
[[1, 2, 3],
 [4, 5, 6]]
and
[[7, 8],
 [9, 10],
 [11, 12]]
Their product will be:
[[58, 64],
 [139, 154]]
```



Q4. Given a list of integers as an input, print a list containing the double of all the even numbers in the list and the sum of the elements of this new list. You may compute the sum using the sum() library function (you do not need import math to use it).

```
Test Case 1:
Input:
4, 5, 3, 2, 6, 4, 1
Output:
[8, 4, 12, 8]
32
Explanation:
The even numbers in the list are 4, 2, 6, 4.
Their doubles are 8, 4, 12, 8.
The sum of these doubled values is 32.
```



## Hints

Q1

1. The candidates for overall maximum are max(list 1) and max(list 2).
2. The candidates for overall minimum are min(list 1) and min(list 2).



Q2

1. Transpose of m x n matrix will be a n x m matrix.
2. During transpose, `jth` column of original matrix becomes the `jth` row of transposed matrix.



Q3

1. To multiply m1 x n1 matrix and m2 x n2 matrix, n1 should be equal to m2.
2. Result of multiplying m1 x n1 matrix and m2 x n2 matrix is a m1 x n2 matrix.
3. Element at i,j of resultant matrix is formed by multiplying `ith` row of `mat1` and `jth` column of `mat2` elementwise and then taking summation of those products.



Q4

1. Iterate through the given list and collect even numbers in a result list after doubling them.
2. sum() is a built-in function in Python that can return the sum of all elements in an iterable (lists, tuples, etc.).



## Solutions

```python
# Q1
str1 = input()
lst1 = [int(x) for x in str1.split(", ")]

str2 = input()
lst2 = [int(x) for x in str2.split(", ")]


max_lst1 = max(lst1)
max_lst2 = max(lst2)

min_lst1 = min(lst1)
min_lst2 = min(lst2)

max_overall = max(max_lst1, max_lst2)
min_overall = min(min_lst1, min_lst2)


print(max_overall)
print(min_overall)
```



```python
# Q2
m = int(input())
n = int(input())

# m x n matrix
mat = []

# Taking input
str1 = input()
lst1 = [int(x) for x in str1.split(", ")]

# i, j th element of matrix can be found at index i*n+j of lst1
for i in range(m):

    row = []  # Fill the ith row

    for j in range(n):
        row.append(lst1[i*n+j])
    
    mat.append(row)


# print(mat)

""" Computing the transpose """

transpose = []

# Transpose of m x n matrix will be a n x m matrix.
# In transpose, jth column of original matrix becomes the jth row of transposed matrix

for j in range(n):
    # Get the jth column of og matrix
    # Make it the jth row of transpose
    new_row = []
    for i in range(m):
        new_row.append(mat[i][j])
    transpose.append(new_row)

print(transpose)
```



```python
# Q3
""" Input matrix 1 """

m1 = int(input())
n1 = int(input())

# m1 x n1 matrix
mat1 = []

# Taking input
str1 = input()
lst1 = [int(x) for x in str1.split(", ")]

# i, j th element of matrix mat1 can be found at index i*n1+j of lst1
for i in range(m1):
    row = []  
    for j in range(n1):
        row.append(lst1[i*n1+j])
    mat1.append(row)


""" Input matrix 2 """

m2 = int(input())
n2 = int(input())

# m2 x n2 matrix
mat2 = []

# Taking input
str2 = input()
lst2 = [int(x) for x in str2.split(", ")]

# i, j th element of matrix mat2 can be found at index i*n2+j of lst2
for i in range(m2):
    row = []  
    for j in range(n2):
        row.append(lst2[i*n2+j])
    mat2.append(row)


""" Matrix Multiplication """

def mat_mul(mat1, mat2):
    m1 = len(mat1)
    n1 = len(mat1[0])

    m2 = len(mat2)
    n2 = len(mat2[0])

    if(n1 != m2):
        print("Invalid dimensions")
        return
    
    mat = []  # of dims m1 x n2

    for i in range(m1):
        row = []
        for j in range(n2):
            # element at i,j of resultant matrix is formed by multiplying 
            # ith row of mat1 and jth column of mat2 elementwise and taking 
            # summation over it
            elem = 0
            for k in range(n1):
                elem += mat1[i][k] * mat2[k][j]
            
            row.append(elem)
        
        mat.append(row)
    
    return mat


print(mat_mul(mat1, mat2))
```



```python
# Q4
# Taking a list as input
str1 = input()
lst = [int(x) for x in str1.split(", ")]

# Result list
res_lst = []

# Iterate through given list
for num in lst:
    if num%2 == 0: # Take only even numbers
        res_lst.append(num*2)

print(res_lst)

print(sum(res_lst))  # to find the sum of all values of list
```

