---
title: "error: stdio.h: No such file or directory"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by shaynaynay on 2005-11-27
How could it be?!
When I head ubuntu 5.04 I installed GCC from the packet manager, with all it's dependings, and it worked fine. I was able to compile all my C programs with no problem.

I installed ubuntu 5.10 (clean install) and again installed the GCC... but now when I'm compiling my progs, i get this error:
```
error: stdio.h: No such file or directory
```
So, what is going on? where is this file...? what is the problem?

Man, I need this!!

Thank you guys,
Guy.

---

### Post by shaynaynay on 2005-11-27
Well, I kinda found answer to my question.
I downloaded libc6-dev (if I recall) and that fixed that problem.

But now I'm getting this:

```
guest@ubuntu:~/ex1$ gcc ex1.c -Wall -o t
/usr/lib/gcc/i486-linux-gnu/4.0.2/../../../../lib/crt1.o: In function `_start':
../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
```

That I cannot solve on my own...
So, I need your help folks...

---

### Post by TheStoneman on 2008-06-19
Somehow I assumed that I would be able to compile a basic C program on any linux box - I mean unices are useful like that, right? So I was a bit surprised when I decided to compile a bit of C just now (in fact Christian Wolff's neat little mp3cut tool) and was faced with the following errors:

chris@snackerjack-lx:/usr/src/mp3cut-0.8$ make
gcc -o mp3cut mp3cut.c
mp3cut.c:25:19: error: stdio.h: No such file or directory
mp3cut.c:26:20: error: stdlib.h: No such file or directory
mp3cut.c:27:20: error: string.h: No such file or directory
mp3cut.c:28:20: error: unistd.h: No such file or directory

..etc .. etc


So what kind of unix comes with make and a compiler, but none of the required dev libraries and headers required to make any normal C program work? Well a brief google yielded the following solution.. Yup, you guessed it.. you need to install a dev package:

sudo apt-get install build-essential


Excuse my rant, but if it's so 'essential', then why isn't it installed as part of the core system? I find that kinda weird. Anyway, problem fixed and C-sources are now compiling.

COURTESY
TheStoneman

---

