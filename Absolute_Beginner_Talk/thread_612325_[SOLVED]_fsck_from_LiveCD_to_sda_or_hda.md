---
title: "[SOLVED] fsck from LiveCD to sda or hda"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-13
Somebody, please, I'm running the LiveCD and need to do something on the command line to fsck my 2 hard drives.

ubuntu@ubuntu:~$ 

is what the LiveCD session terminal says. Do I need to log in as root? How?


The BIOS and Grub got unhappy with one another, and I'm looking for a solution.

---

### Post by PointyWombat on 2007-11-13
It's not really clear what your problem is here, but if you need to drop down into the root shell, just:

$ sudo su -

then do what you need to do. But what are you trying to solve?

PointyWombat

---

### Post by Mark_in_Hollywood on 2007-11-14
From a LiveCD session I wanted to "do" a file system check, aka: fsck, on (or against) my two hard drives, hd0, hd1 (aka: sd0, and sd1).

I've given up on the idea of that. Thanks.

---

