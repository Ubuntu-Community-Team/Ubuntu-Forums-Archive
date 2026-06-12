---
title: "Is it possible to reinstall ubuntu by console?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by xeth on 2007-10-19
While learning to use ubuntu, I've accumulated junk and broken ubuntu many times. Now that it's released finally I would like to do a clean install.

Is it possible to do an install by console like sudo apt-get install ubuntu? I tried to do a sudo apt-get install ubuntu-desktop but it wasn't the same.

My Home is on a different parition, so if I reinstalled ubuntu and placed the Home on the old Home partition, it won't be deleted or over written correct?All the files that are on the old Home partition would be intact.

How do you force install or force repair a package or program when it's broken? I've come across a package that when I do a sudo apt-get remove, sudo apt-get autoremove, it removes a 40kb file and finishes and I remember that when it installed, it installed many files.

---

### Post by crimesaucer on 2007-10-20
A clean install is when you burn an iso image to CD and install it that way, erasing all of you old system.

A console (terminal) install is the same as the upgrade button, but not as good because of dependencies.

You should use the upgrade button or do a clean install with a CD. 


I would use a CD from torrent, then install that way. You can format your partition with GPARTED.

---

### Post by dcstar on 2007-10-20
> **xeth said:**
> 
..........
My Home is on a different partition, so if I reinstalled Ubuntu and placed the Home on the old Home partition, it won't be deleted or over written correct?All the files that are on the old Home partition would be intact.
..........

Correct -** if** you don't let the partitioner wipe you existing partitions!

I just installed Gutsy and I kept my existing partitions (including my separate /home partition) using the Manual partition option during the install, all was ok on boot up to the new system.

Just make a note of where your /home partition is on your disk so you can set it up when in the manual partition phase.

---

