---
title: "OSX can't see my fat32 partition"
date: 2007-07-08
forum: Apple Intel Users
---

### Post by darkmaster on 2007-07-08
Hi everyone, this might be a really simple problem but I'm not able to solve it, wonder why.
I own a new macbook and used bootcamp to reduce the osx partition to a little one, then booted with Ubuntu Live CD and splitted the remaining part of free space in 2 main partitions: one for Ubuntu and one to use as common data storage between Ubuntu and OSX. The idea is fine for me but...
So the common partition is formatted in Fat32 and I told ubuntu to mount it in /common. It is readable, writable, all OK and in Ubuntu I can work with this parition well.
In OSX it is not automatically mounted. Even if it is a fat32. I was ready to bet that OSX would have noticed the existence of this partition and automounted it as it does with USB keys but I was wrong. How to I have OSX see this partition?

---

### Post by cyberdork33 on 2007-07-10
Sorry, nobody is answering. I am not sure why it is not mounting. Can you open up disk Utility and see if it is listed? maybe you can mount it from there?

---

### Post by ronocdh on 2007-07-10
Well, in Ubuntu it's as simple as editing /etc/fstab. Probably there is something similar in OS X, no? 

... Or not: I just poked around in OS X, check this out:
```
sudo nano /etc/fstab
```
This yields a blank file! That can't be right... so I tried:
```
cd / && ls
cd etc && ls
```
Ah-ha! "fstab.hd," it's called. So I rerun the initial command with the extension added, and check out the contents of the file:
> IGNORE THIS FILE.
This file does nothing, contains no useful data, and might go away in
future releases.  Do not depend on this file or its contents.
:( That sucks. Clearly OS X is doing it differently. Maybe there's a comparable file associated with Disk Utility?

---

### Post by cyberdork33 on 2007-07-10
As was noted in another thread (Home partition sharing?), /etc/fstab does not exist, but if you create it and put the entry in it, it will still work. You really should try to do it the "OSX way" though as I don't know if mounting via fstab will have it show up as a mounted volume with an icon like a USB drive, or the OSX partition, etc.

---

### Post by Gen2ly on 2007-07-11
If you format the partition in OSX it is mounted on the desktop in OS X and Ubuntu see this:

[http://gentoo-wiki.com/HARDWARE_Apple_MacBook#FAT32](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#FAT32)

---

