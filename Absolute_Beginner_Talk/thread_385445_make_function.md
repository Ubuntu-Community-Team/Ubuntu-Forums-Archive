---
title: "make function"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Monsoonx27 on 2007-03-15
can someone explain the make function to me 
i know it complies but how to use it properly with example please

---

### Post by coffeeadikt on 2007-03-15
In a nutshell the make command is used to compile and install a program from source.

*make* by itself will compile whatever is in the directory that you run it in. It will look for a file called "Makefile" to get instructions from also. This can be done as a regular user. The binary program that it creates can usually be run locally.

*make clean* will erase all the compiled binaries and header files that *make* created - effectively returning you to square one. This only works locally so you can do it as a regular user.

*make install* will move the compiled binaries into the system user space thus making the program available to all users. Since the user space is protected, you need *sudo* to run *make install*

*make uninstall* will erase the compiled binaries from the system user space. You need *sudo* to run *make uninstall* and this will remove the program for all users.

This is the very high level guide. If you need more detail type

$ man make

at the command line.

---

### Post by Monsoonx27 on 2007-03-15
their is no make file generated 
i extracted the tar.bz2
then
./configure

and i am trying to make when (no makefile found or no target)

---

### Post by Monsoonx27 on 2007-03-15
the problem turned out to being a messed up package

---

