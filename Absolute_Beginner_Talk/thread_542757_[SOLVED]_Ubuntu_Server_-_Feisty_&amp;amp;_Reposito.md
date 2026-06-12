---
title: "[SOLVED] Ubuntu Server - Feisty &amp;amp; Repositories"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-09-04
I am trying to install a network monitoring tool called ntop.
I have added these repositories:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

But when run: sudo apt-get install ntop

It asks me to insert the 7.04 Server Cd.  My server is at home, and I am at work. 

Its obvious what my problem is, how do I fix it?

Thanks

---

### Post by az on 2007-09-04
ntop probably depends on a package that is on the install cd.  Comment-out the cdrom line at the top of your sources.list.

Run
sudo apt-get update
 and you should be able to install ntop from the net.

---

### Post by lmlypfan on 2007-09-04
Worked perfectly.

THANKS!

---

### Post by Miguel on 2007-09-04
If you open your /etc/apt/sources.list file, you will see a line mentioning a cd-rom (usually at the top). You should comment it with a #. After that, update your sources (sudo aptitude update). trying to install ntop now should work.

EDIT: Too late.

---

