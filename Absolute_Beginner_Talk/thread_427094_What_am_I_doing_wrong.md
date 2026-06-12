---
title: "What am I doing wrong?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-04-29
Ever since I've had Ubuntu  I've been trying to install a tarball...without success.  I've looked  through  the forum  and checked several websites but I must be doing something wrong.   Please help.  Thanks

[http://www.freeimagehost.eu/image/376c70288763]("http://www.freeimagehost.eu/image/376c70288763")

---

### Post by Najand on 2007-04-29
It means your file doesn't exist. You can use "ls" command and see if it is there or not... If you have downloaded it from the internet, firefox usually downloads files on the ~/Desktop not on your home(~).
Try to find the file and try it again.

---

### Post by DrPppr242 on 2007-04-29
Your screenshot shows the file on your desktop not your home directory
you need to switch to the desktop by typing
cd Desktop
then unpack the file
tar xzvf "file name including .tar.gz"
then the file probably has a readme or install file with instrucitons but usually the commands are
./configure
make
make install
to install the program

---

### Post by jtx472 on 2007-04-29
Thank  you Dr Pepper.  That worked.

---

