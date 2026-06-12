---
title: "C compile problem with gcc"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by cobweb on 2006-02-07
hi,

i cannot compile c files with gcc from the command-line, when i try the error message is:
first.c:1:19: error: stdio.h: No such file or directory

it is most probably because the gcc compiler cannot find any C libraries, i actually do not know even one is already installed or not. i just installed gcc by saying
apt-get install gcc, that is all...

what can i do?
thanx in advance..

---

### Post by nixclusive on 2006-02-07
Try installing the libc6 library:

apt-get install libc6

more info here:
[http://packages.ubuntu.com/breezy/base/libc6](http://packages.ubuntu.com/breezy/base/libc6)

Hope it helps...

---

### Post by paulmilliken on 2006-02-07
First, check if stdio.h really isn't on your computer.  To do this do:
"cd /
sudo find -name stdio.h"

Paul

---

### Post by Perfect Storm on 2006-02-07
```
sudo apt-get install build-essential
```
Gives you the basic/foundation for compiling.

---

### Post by cobweb on 2006-02-07
[QUOTE=Artificial Intelligence]```
sudo apt-get install build-essential
```
Gives you the basic/foundation for compiling.[/QUOTE]

thanks this worked for compilation, an a.out file is constructed in the same directory, but when i type a.out on the command-line, 
bash: a.out: command not found
is printed, so i cannot get an output.

and in the directory of a.out, a lock symbol appears on the up-right corner of the executable. 

now what is the problem,
thanks a lot

---

### Post by Perfect Storm on 2006-02-07
What excatly are you trying to do or compile?

---

### Post by cobweb on 2006-02-07
i am just compiling a very simple c program, a single file i mean..

the output is some text, just playing around with the compiler...

---

### Post by nixclusive on 2006-02-07
when i have saved a program i enter

cc prog.c
./a.out

and the output is displayed.

---

### Post by cobweb on 2006-02-07
./a.out worked perfect, thank you nixclusive

---

### Post by davidco90 on 2008-01-23
> **Artificial Intelligence said:**
> ```
sudo apt-get install build-essential
```
Gives you the basic/foundation for compiling.

when I try to install this in terminal i recive this error :
> All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

how can i fix it??

---

