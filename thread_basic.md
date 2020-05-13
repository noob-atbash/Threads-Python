In computer science, a thread of execution is the smallest sequence of
programmed instructions that can be managed independently by a scheduler,
which is typically a part of the operating system.The implementation
of threads and processes differs between operating systems, but in most
cases a thread is a component of a process. Multiple threads can exist
within one process, executing concurrently and sharing resources such as
memory, while different processes do not share these resources. In
particular, the threads of a process share its executable code and the
values of its dynamically allocated variables and non-thread-local global
variables at any given time,for detailed theory on Thread [click here](https://en.wikipedia.org/wiki/Thread_(computing))

**In simple words it is a path of execution within a process ..**

###### MULTITHREADING
---

Its main idea is to achieving the idea of parallelism , it divides a work
into many threads for the different parts of the work .Let the work has 5 parts, so the work will be divided between 5 threads for faster work.Threads do not execute parallelly, they just switch between one another.

>LET UNDERSTAND THREADS WITH THE HELP OF PYTHON

Thread class comes in threading module in python,please read the
[official documenration](https://docs.python.org/2/library/thread.html) to grasp some concepts.

---

Let us take the helloworld program for threads

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

#importing threading module
import threading
#importing time module
import time

def func(name):
    print ("Hi,its {}\n".format(t.name),end="")
    time.sleep(3)
    print ("{} is now active".format(name))

#t is a thread for the function "func" , it has mainly 3
#parameters , 1st parameter is the target function,
#2nd parameter is the name of the thread
#3rd parameter is the args of the function in the form of a tuple

t = threading.Thread(target = func, name = 'Thread1', args = ("Thread1",))

#start() function starts the thread

t.start()

```

<code>OUTPUT</code>
```
Hi,its Thread1
Thread1 is now active
```
> You can execute the file by python3 thread_basic.py or ./thread_basic.py (before executing chmod a+x thread_basic.py)


Let us understand another thing

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

#importing threading module
import threading
#importing time module
import time

def func(name):
    print ("Hi,its {}\n".format(t.name),end="")
    time.sleep(3)
    print ("{} is now active".format(name))

#t is a thread for the function "func" , it has mainly 3
#parameters , 1st parameter is the target function,
#2nd parameter is the name of the thread
#3rd parameter is the args of the function in the form of a tuple

t = threading.Thread(target = func, name = 'Thread1', args = ("Thread1",))

#start() function starts the thread

t.start()

print ("In Main function, executed before the function ends...")

```
<code>OUTPUT</code>

```
Hi,its Thread1
In Main function, executed before the function ends...
Thread1 is now active

```

You can see the main function executed before the function ended
here join() function comes in

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

#importing threading module
import threading
#importing time module
import time

def func(name):
    print ("Hi,its {}\n".format(t.name),end="")
    time.sleep(3)
    print ("{} is now active".format(name))

#t is a thread for the function "func" , it has mainly 3
#parameters , 1st parameter is the target function,
#2nd parameter is the name of the thread
#3rd parameter is the args of the function in the form of a tuple

t = threading.Thread(target = func, name = 'Thread1', args = ("Thread1",))

#start() function starts the thread

t.start()
t.join()

print ("In Main function, executed before the function ends...")

```

<code>OUTPUT</code>
```
Hi,its Thread1
Thread1 is now active
In Main function, executed before the function ends...
```
join() function waits for the function to end then moves to the main function

###### MULTITHREADING
---

```python
threads_list = []

start = time.time()

for i in range(5):
    t = threading.Thread(target = func, name = 'thread{}'.format(i+1), args = ('thread{}'.format(i+1),))
    threads_list.append(t)
    t.start()
    print ("{} has started".format(t.name))

for t in threads_list:
    t.join()

end = time.time()

print ("time taken: {}".format(end-start))

print ("all live threads finished job")

```
<code>OUTPUT</code>
```
Hi,its thread1
thread1 has started
Hi,its thread2
thread2 has started
Hi,its thread3
thread3 has started
Hi,its thread4
thread4 has started
Hi,its thread5
thread5 has started
thread1 is now active
thread5 is now active
thread3 is now active
thread4 is now active
thread2 is now active
time taken: 3.0047194957733154
all live threads finished job

```
Author - [Kakí_epíthesi](https://github.com/kaki-epithesi)

[ALL CODES](https://github.com/kaki-epithesi/Python-Threads) 