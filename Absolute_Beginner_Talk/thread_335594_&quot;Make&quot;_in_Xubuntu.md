---
title: "&quot;Make&quot; in Xubuntu?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by rashby on 2007-01-10
Previously (a couple of years ago) I worked in an AIX environment, where we used "make" to build applications in C.

I just downloaded a pre-built Xubuntu virtual machine to run from VMware.

I then copied some C source code into the file system and tried "make -f Makefile", and I was told the make command was not found.

So, is there some equivalent to make in Xubuntu.

Alternatively, do I need to download make from somewhere?

Thanks very much

---

### Post by viciouslime on 2007-01-10
Yup, just install the build-essentials package. This will install make for you, along with other things needed for compiling programs.

---

### Post by doobit on 2007-01-10
> **rashby said:**
> Previously (a couple of years ago) I worked in an AIX environment, where we used "make" to build applications in C.

I just downloaded a pre-built Xubuntu virtual machine to run from VMware.

I then copied some C source code into the file system and tried "make -f Makefile", and I was told the make command was not found.

So, is there some equivalent to make in Xubuntu.

Alternatively, do I need to download make from somewhere?

Thanks very much

make is part of the build essentials package. You need to download and install build essentials to make make available! Type in a terminal
sudo apt-get install build-essential

---

