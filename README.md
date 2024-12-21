Operating-Systems-Monsoon-2024-Assignments                                        
--------------------------------------------

-> List of all OS 2024 Assignments

Assignment 1
--------------

Q1: Parent Process with 7 Children
- Objective: Create a parent process that forks 7 child processes. Each child generates 4 random numbers between 1 and 100, calculates their mean, and prints it. The parent waits for all children to finish before returning.
- Key Concepts: Forking processes, process synchronization, `wait()` system call.

Q2: Binary Search Using Forked Processes
- Objective: Perform binary search on a 16-element sorted array by forking child processes. The parent defines the array, asks the user for a target value, and the children work on portions of the array. The child that finds the target value prints its index.
- Key Concepts: Forking processes, binary search, inter-process communication.

Q3: System Utility Commands (`date`, `cal`, `uptime`)
- Objectiv: Implement the `date`, `cal`, and `uptime` commands in C. The `main.c` program forks 3 child processes to execute each command using `exec()`. The parent waits for the children to finish.
- Key Concepts: `fork()`, `exec()`, system calls, process management.
- Files:
  - `date.c`: Simple date command implementation.
  - `cal.c`: Calendar command using Zeller's congruence.
  - `uptime.c`: Uptime command using `sysinfo()`.

Q4: CPU Scheduling Algorithms
- Objective: Simulate four CPU scheduling algorithms: FIFO, SJF, SRTF, and Round Robin. The program calculates the order of execution and the average response time and turnaround time for each algorithm.
- Key Concept: Scheduling algorithms, process management, time quantum, performance metrics.


# Operating Systems - Monsoon 2024 Assignment 2
--------------------------------------------------


Q1: Parallel Merge Sort on 16-Element Array [10 pts]
- Objective: Perform parallel merge sort on a 16-element unsorted array. The array will be divided into smaller arrays and passed to child processes, which will merge the arrays after sorting.
- Key Concepts: Forking processes, merge sort, inter-process communication using pipes.
- Input: A 16-element unsorted array defined in the code.
- Output: Prints the initial unsorted array and the final sorted array.

Q2: Segmentation and Address Translation [20 pts]
- Objective: Simulate memory management using segmentation and address translation. Raise segmentation faults when the logical address exceeds the segment's bounds.
- Design:
  - 64KB physical memory divided into Code, Heap, and Stack segments.
  - Code segment starts at 32KB, Heap at 34KB, and Stack at 28KB.
  - Raise a segmentation fault if the offset exceeds the segment's limit.
- Input: User enters a 16-bit logical address in hexadecimal format (e.g., a56f).
- Output: Physical address in hexadecimal format or a segmentation fault.

Q3: Paging-Based Memory Management with TLB [20 pts]
- Objective: Simulate address translation using a page table and a Translation Lookaside Buffer (TLB). Handle TLB misses by fetching the translation from the page table.
- Design:
  - Simulate a page table with a 64KB total memory and 4KB page size.
  - TLB caches recent translations to speed up the translation process.
- Input: User enters a 16-bit logical address in hexadecimal format (e.g., a56f).
- Output: Physical address in hexadecimal format and a TLB hit or miss message.

Q4: Two-Level Page Table for Virtual Memory Management [20 pts]
- Objective: Simulate address translation using a two-level page table. Implement page directory and page tables to handle memory access.
- Design:
  - The virtual address is divided into three parts: Page Directory Index, Page Table Index, and Offset.
  - Implement functions to load and store data at virtual addresses and simulate page faults.
- Input: 32-bit virtual address.
- Output: Physical address or page fault message.                                        
  

Q5: Memory Management with Clock Algorithm [30 pts]
- Objective: Simulate memory management with page faults using the clock algorithm for page replacement. Track page hits and page faults.
- Design:
  - Simulate a memory system with N pages using a fixed-size page table.
  - Handle page requests and replace pages using the clock algorithm, considering the reference and dirty bits.
- Input: 
  - `num_frames`: Number of memory frames.
  - `page_requests`: A string representing the sequence of page requests.
- Output: Total page faults, total page hits, and hit rate.




# Assignment 3: Multithreading and Synchronization (Monsoon 2024)
--------------------------------------------------------------------

## Overview
This assignment involves creating C programs that simulate various real-world problems using threads and synchronization mechanisms like semaphores and mutexes. The assignment aims to deepen your understanding of multithreading concepts, deadlock prevention, resource management, and matrix operations with concurrency.

---

---

Question 1: Thread Scheduling and Deadlock Avoidance [25 points]

Objective:
Simulate a thread scheduling system where multiple threads (T1, T2, T3) acquire two locks (Lock A and Lock B) in a predefined order, ensuring deadlock avoidance.

Design:
- Threads: 3 threads (T1, T2, T3).
- Locks: Two locks (Lock A, Lock B).
- Deadlock Avoidance: Implement resource instance ordering where Lock A must always be acquired before Lock B.
- Output: Print the order of lock acquisition and thread waiting states.

Input:
None

Output:
- Display messages indicating lock acquisition and thread waiting states:
  - Example: "T1 acquired Lock A", "T2 waiting for Lock A".
- Each thread should acquire each lock 3 times.

Notes:
- This program ensures deadlock-free execution using a strict lock acquisition order.

---

Question 2: Networked Servers Problem [25 points]

Objective:
Simulate a networked server system where multiple servers (5 in total) access shared network channels with mutual exclusion and starvation prevention using semaphores.

 Design:
- Servers: 5 servers, each needing access to two adjacent network channels.
- Synchronization: Use semaphores for mutual exclusion and to prevent starvation.
- Processing Time: Each server takes 1 second to process data.
- Output: Print messages for each server's state (waiting, processing).

Input:
None

Output:
- Example: "Server 1 is processing", "Server 2 is waiting".

Notes:
- Each server should process data 3 times, and the system should ensure no starvation.

---

Question 3: Warehouse Management System [25 points]

Objective:
Simulate a warehouse inventory management system where delivery trucks and storage managers operate concurrently, managing limited storage capacity using semaphores/mutexes.

Design:
- Storage: A circular buffer represents the warehouse storage with a fixed capacity.
- Delivery Trucks: Trucks deliver products randomly, and wait if storage is full.
- Storage Managers: Manage the storage by taking products from the buffer, waiting if the buffer is empty.
- Synchronization: Use semaphores/mutexes to manage access to the buffer.
- Output: Display the inventory status and buffer state after each operation.

Input:
- Number of delivery trucks and storage managers.
- Buffer size defined as a constant.

Output:
- Messages indicating the current inventory status after each delivery and storage operation.
- Demonstrate synchronization issues like buffer overflows or underflows.

Notes:
- The system should prevent race conditions and ensure proper coordination.

---

Question 4: Matrix Multiplication with Threads [25 points]

Part 1: Matrix Multiplication Using Threads
Objective:
Perform matrix multiplication by dividing the work among multiple threads, each calculating one element of the resultant matrix.

Design:
- Matrices: Matrix A (m x n), Matrix B (n x p), Resultant matrix C (m x p).
- Threads: Create a thread for each element in matrix C.                    
  
- Output: Display the resultant matrix C and speed up comparison with sequential matrix multiplication.

Input:
- Matrix dimensions and the elements of matrices A and B.

Output:
- Resultant matrix C and speed up over sequential version.

Notes:
- The program divides the matrix multiplication task into smaller sub-tasks, each handled by a separate thread.

---

Part 2: Thread Pool for Matrix MultiplicationObjective:
Optimize matrix multiplication by reusing threads through a thread pool, avoiding the overhead of creating new threads for each element.

Design:
- Thread Pool: Manage a fixed number of threads using the pthreads API.
- Callback Design: Create a generic thread pool API that accepts a callback function to perform matrix multiplication tasks.
- Output: Display the resultant matrix C and speed up comparison with both the sequential and part 1 implementations.

Input:
- Same as Part 1 (matrix dimensions and elements).

Output:
- Resultant matrix C and speed up analysis.

Notes:
- This part focuses on optimizing the matrix multiplication process using a thread pool.

---

Here's a sample README for the **Operating Systems - Monsoon 2024** Assignment:

---

                                        
  
Assignment 4
--------------------------------------

Overview
This repository contains the solutions for the **Operating Systems - Monsoon 2024** Assignment 4. It includes implementations for various system-level programming tasks such as file handling, disk scheduling, process management, and command simulation using C programming language. The following are the solutions to the questions as outlined in the assignment.



Q1: Temperature Measurement Calculation (20 points)

Objective:
Write a program in C to retrieve temperature measurements from a text file and calculate the min, mean, and max temperatures per weather station. Implement two variations of the program using `mmap` and `fread` (or any file read function).

Input:
A text file containing 50 million rows of weather station data with the following format:

```
station_name;temperature
```

Output:
For each weather station, output the minimum, mean, and maximum temperatures.

Example:
```
Delhi min=29.6 mean=30.25 max=31.0
```

Deliverables:
- Q1.c: Implementation of the program using `fread` and `mmap`.                    
  
- Makefile to compile the program.
- A small writeup explaining the differences between `mmap` and `fread` in terms of efficiency for this dataset.

---

Q2: Shortest Seek Time First (SSTF) Disk Scheduling (15 points)

Objective:
Simulate the Shortest Seek Time First (SSTF) disk scheduling algorithm. Calculate both seek time and rotational latency for a given set of requests.

Input:
The disk request queue containing the requested disk sectors.

Example:
```
Disk requests: 78 289 21 495
```

Output:
For each request, calculate and print:
- Seek Time
- Rotational Latency

---

Q3: Random Access with `lseek` System Call (15 points)

Objective:
Use the `lseek` system call to randomly access file data and retrieve specific records from a binary file.

Input:
Create a `students.rec` binary file containing records of 5 students. Each record contains:
```
struct Student {
    int id;
    char name[20];
};
```

Output:
Based on the user input, retrieve and print the student’s name from the binary file.

Example:
```
Enter student ID: 3
Student name: John Doe
```

---

Q4: Output Redirection Using `dup` System Calls (20 points)

Objective:
Simulate output redirection using the `dup`, `dup2`, and `dup3` system calls.

Part 1: Simple Output Redirection
- Implement a function that opens a file for writing and uses `dup` or `dup2` to redirect `stdout` to the file.
- Print some random text to the redirected stdout and verify that the data is written to the file.

Part 2: Interactive Simulation
- Simulate a simple shell-like command that redirects the `stdout` and `stderr` of any internal command into a file.

---

Q5: Simulation of Common Shell Commands (30 points)

Objective:
Create a folder `q5` containing simple implementations of the following shell commands:
1. list.c: Implements the `ls` command to list the files in the directory.
2. countw.c: Implements the `wc` command to count words in a file.
3. copy.c: Implements the `cp` command to copy a file to a directory.
4. move.c: Implements the `mv` command to move contents from one directory to another.
5. main.c: Runs all of the above commands as child processes using `fork`, `wait`, and `exec` functions.

---

Makefile

A Makefile is provided for compiling the programs. The following targets are available:
- `make`: Compiles all the C programs.
- `make clean`: Cleans up the generated object files and executables.

---

## Compiling and Running

1. **To compile all the programs**:
   ```
   make
   ```

2. **To run the programs**:
   - For Q1: 
     ```
     ./q1
     ```
   - For Q2:
     ```
     ./q2
     ```
   - For Q3:
     ```
     ./q3
     ```
   - For Q4:
     ```
     ./q4 -p1 output_p1.txt
     ./q4 -p2 "ls -l" output_p2.txt
     ```
   - For Q5:
     ```
     cd q5
     make
     ./main
     ```

---

