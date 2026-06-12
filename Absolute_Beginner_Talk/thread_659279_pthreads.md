---
title: "pthreads"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-05
What are pthreads, and how do I make sure that they are installed?  If they are not installed, how do I install them?

---

### Post by mattismyname on 2008-01-07
Hi.

First off, what is a thread?  Read here: [http://en.wikipedia.org/wiki/Thread_%28computer_science%29](http://en.wikipedia.org/wiki/Thread_%28computer_science%29)

What are pthreads?  pthreads is short for POSIX Threads.  A specific API (application programming interface) allowing a program to create and manipulate its own threads.  Read more here: [http://en.wikipedia.org/wiki/Pthreads](http://en.wikipedia.org/wiki/Pthreads)

So, do you have pthreads?  Well, if you have the standard gnu compilers & glibc installed on your Ubuntu system, then you have pthreads.  An easy way to see if you're able to compile a program that requires pthreads is to run the following command and see the same output I do:

```
matt@Aluminumy:~/Desktop$ locate pthread.h
/usr/include/pthread.h

```

If there's a specific problem you're having, you could elaborate more.

---

