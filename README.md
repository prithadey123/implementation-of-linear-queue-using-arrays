 Overview
This project demonstrates the implementation of a **Queue data structure using an array** in C.

A Queue follows the **FIFO (First In, First Out)** principle:
- The first element inserted is the first element removed.

This program implements:
- ✅ Enqueue Operation (Insertion)
- ✅ Dequeue Operation (Deletion)
- ✅ Display Operation
- ✅ Overflow and Underflow Handling

---

 Source Code

```c
#include <stdio.h>
#include <stdlib.h>

#define MAX 5

int queue[MAX];
int front = -1;
int rear = -1;

// Enqueue operation
void enqueue(int value) {
    if (rear == MAX - 1) {
        printf("Queue Overflow! Cannot insert %d\n", value);
        return;
    }

    if (front == -1)
        front = 0;

    rear++;
    queue[rear] = value;
    printf("%d inserted into queue\n", value);
}

// Dequeue operation
void dequeue() {
    if (front == -1 || front > rear) {
        printf("Queue Underflow! Queue is empty\n");
        return;
    }

    printf("%d removed from queue\n", queue[front]);
    front++;

    // Reset queue when empty
    if (front > rear) {
        front = rear = -1;
    }
}

// Display queue
void display() {
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }

    printf("Queue elements are:\n");
    for (int i = front; i <= rear; i++) {
        printf("%d ", queue[i]);
    }
    printf("\n");
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    display();

    dequeue();
    display();

    return 0;
}
```

---

 Explanation

 Queue Declaration
- `#define MAX 5` → Maximum size of queue.
- `queue[MAX]` → Array used to store queue elements.
- `front` → Points to the first element.
- `rear` → Points to the last element.

 Enqueue Operation
- Checks for **Overflow** (`rear == MAX - 1`).
- If queue is empty, initializes `front = 0`.
- Increments `rear` and inserts the value.

 Dequeue Operation
- Checks for **Underflow** (`front == -1 || front > rear`).
- Removes element from `front`.
- Increments `front`.
- Resets queue when empty.

 Display Operation
- Prints elements from `front` to `rear`.

---

 Sample Output

```
10 inserted into queue
20 inserted into queue
30 inserted into queue
Queue elements are:
10 20 30
10 removed from queue
Queue elements are:
20 30
```

---

 Time Complexity

- Enqueue: **O(1)**
- Dequeue: **O(1)**
- Display: **O(n)**

---

 How to Compile and Run

 Compile:
```
gcc queue_array.c -o queue
```

 Run:
```
./queue
```

---

 Concepts Used
- Arrays in C
- Queue Data Structure
- FIFO Principle
- Overflow & Underflow Conditions
- Functions in C
