---
title: "Help needed with GNU C and g77"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by nuwan78 on 2006-04-19
Hi guys,

   I am new to linux and also to ubuntu. I was successful in installing ubuntu 5.10 ( breezy badger) and I intalled GNU C too. However I don't know how to access the compiler through a terminal. Can anyone explain the right way?

  Also I tried to install g77 by coding $ sudo apt-get install g77 with the installation CD ( 5.10) inside my CD drive, however the terminal gave the message " couldn't find package g77 ) What's wrong? please explain and give a remedy or advice.

Thanks

Nuwan K.

---

### Post by htinn on 2006-04-19
The Breezy Install CD only has GCC 3.3/4.0 (of cpp, g++, and gij). For g77, you'll need to connect to the internet and download it.

---

### Post by uteck on 2006-04-19
The man page for gcc may help a bit, In a terminal type "man gcc".  Most packages have a manual page that is accessed by typing 'man' and the package name.

---

### Post by IYY on 2006-04-19
g77 is avaliable through apt-get, but you need to be connected to the internet. gcc is also not installed by default, but it is on the CD. To get it, 

sudo apt-get install build-essential

To use it, just do this:

gcc myprogram.c

or 

cc myprogram.c

---

### Post by nuwan78 on 2006-04-21
Thanks guy with the help on GNU C

However, I dont have internet connction so is there an alternate way to get g77
I really need the fortran compiler for linux.


Hope to hear .. soon........

Nuwan

---

