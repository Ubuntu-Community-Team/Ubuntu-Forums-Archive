---
title: "error libmng.so.1"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-03-07
Hi,

    I am trying to install Salome (a meshing software) in a 64bit ubuntu. However, i have the following error

while loading shared libraries: libmng.so.1: wrong ELF class: ELFCLASS64

what does it mean? Does libmng not being supported in 64bit?

I have used locate libmng.so and found that the file has been installed properly.

Any idea?#

---

### Post by osmanb on 2007-08-30
I think the installer wizard is 32 bit and looking for the 32 bit libmng  usually in  /usr/lib32. I have the same problem. But cannot find the 32 bit lib for x86 (not i386). I was able to load quite a bit of the other 32 bit libs but not this one. Have you ]been able to solve this problem???

---

### Post by in_flu_ence on 2007-08-31
[http://ubuntuforums.org/showthread.php?t=369959](http://ubuntuforums.org/showthread.php?t=369959)

I have solved it awhile ago in a 64bit system. I am not exactly sure if it will work the same for you. 

Let's discuss further if you have some trouble.

---

### Post by Fingolfin on 2007-09-26
Some time ago I experienced similar problems with a number of .so files.
The reason was that the OpenGL 3D acceleration has not been properly activated, i.e. the installation of the graphics card driver failed.
If you are sure that your 3D acceleration is working properly, another possible explanation is the incompatibility between 32- and 64-bit components on which the software depends.

---

