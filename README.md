# EIGHT-QUEENS# EXPERIMENT 1(a): IMPLEMENT EIGHT QUEENS PROBLEM

## Aim

To develop a Python program that solves the 8-Queens problem using the Backtracking algorithm. The program should ensure that no two queens attack each other and display valid chessboard configurations.

## Scenario

A chessboard consists of 8×8 squares, and the task is to place 8 queens on the board such that no two queens attack each other.

Queens can attack in horizontal, vertical, and diagonal directions.

### Task Requirements

1. Represent the 8-Queens problem as a Constraint Satisfaction Problem (CSP) or search problem.
2. Implement a solution using Backtracking or Genetic Algorithm.
3. Display valid 8×8 chessboard configurations with queens (Q).
4. Show multiple valid solutions.
5. Compare execution time for different board sizes (4×4, 8×8, 10×10).

## Algorithm / Procedure

1. Start.
2. Initialize an N×N chessboard with all empty positions represented by dots (.).
3. Define an `isSafe()` function to check whether a queen can be placed at a particular position.
4. Check the column, upper-left diagonal and upper-right diagonal.
5. Define a recursive `solve()` function.
6. Place a queen in a safe position.
7. Recursively move to the next row.
8. If no valid position is available, backtrack by removing the previously placed queen.
9. If all N queens are successfully placed, display the solution.
10. Count and display the total number of solutions.
11. Stop.

## Program Code

```python
import copy

N = 8

def printSolution(board):
    for row in board:
        for i in range(N):
            print("Q" if row[i] else ".", end=" ")
        print()
    print()

def isSafe(board, row, col):
    for i in range(row):
        if board[i][col]:
            return False

    for i, j in zip(range(row - 1, -1, -1),
                    range(col - 1, -1, -1)):
        if board[i][j]:
            return False

    for i, j in zip(range(row - 1, -1, -1),
                    range(col + 1, N)):
        if board[i][j]:
            return False

    return True

def solve(board, row, solutions):
    if row == N:
        solutions.append(copy.deepcopy(board))
        printSolution(board)
        return

    for col in range(N):
        if isSafe(board, row, col):
            board[row][col] = 1
            solve(board, row + 1, solutions)
            board[row][col] = 0

def eightQueens():
    board = [[0 for _ in range(N)] for _ in range(N)]
    solutions = []

    solve(board, 0, solutions)

    print(f"Total solutions found: {len(solutions)}")

eightQueens()
```

## Expected Output

The program displays all valid 8-Queens solutions.

### Sample Solution (First Valid Configuration)

```text
Q . . . . . . .
. . . . Q . . .
. . . . . . . Q
. . . . . Q . .
. . Q . . . . .
. . . . . . Q .
. Q . . . . . .
. . . Q . . . .

```

The program continues displaying the remaining valid configurations.

```text
Total solutions found: 92
```

## Result

Thus, the Python program to solve the Eight Queens Problem using the Backtracking algorithm was implemented and executed successfully. A total of 92 valid solutions were found for an 8×8 chessboard.
