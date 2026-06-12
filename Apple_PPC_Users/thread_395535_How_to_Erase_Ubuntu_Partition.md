---
title: "How to Erase Ubuntu Partition?"
date: 2007-03-28
forum: Apple PPC Users
---

### Post by dMac9 on 2007-03-28
Several months ago I downloaded Ubuntu 6.0.6.1 Live CD to try some 3D software. I erased and partitioned my harddrive and Ubuntu installed without too many problems. I tried it, it's nice but I couldn't get any downloaded software to install or run properly because of extra needed files or wrong architecture. Then I bought newer Mac system software and I can run those programs and the partition has been invisible or ignored ever since. I have ExtFSManager installed and I can mount it as read only and trash its files.

Now I want to erase that partition and reclaim the space for the Mac OS, I can see the (9gb) partition but Disk Utility won't erase it. (OS 10.3.9 on a 400mhz iMac, slotloader)

Help!

David

---

### Post by grazie on 2007-03-28
There are a number of different ways to erase unwanted partitions. In my opinion the most user friiendly way to do the job would be to install and use gparted. Apart from creating and deleting, partitions can also be resized. 

A word of caution though. Messing around with partitions is a risky business and ideally shouldn't be done without backups.

---

### Post by dMac9 on 2007-04-20
I finally erased the Ubuntu partition.

I booted up the Live CD and used GParted to format the partition to Fat32. I couldn't use HFS+ and HFS wouldn't format anything over 2gb.

Then I booted up with the OSX 10.3 CD and formated the partition again to HFS+.

Then I booted up to the HD and used Disk Utility to format the partition.

8.9 gb freed up. Now I can use it for OSX or re-install Ubuntu.

David

---

