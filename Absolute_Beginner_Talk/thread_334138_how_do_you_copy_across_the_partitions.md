---
title: "how do you copy across the partitions?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by birdseye on 2007-01-08
How do I copy files from the windows partition to the linux partition and vice versa on a dual boot machine?

---

### Post by azkehmm on 2007-01-08
Do you have all the partitions mounted? 
If so, you can open a nautilus window (the gnome window manager) with sudo-privileges:
```

gksudo nautilus

```
this'll make you able to drag and drop files across partitions and discs as you like.

Please be carfull when using "sudo" or "gksudo" commands, though...

---

### Post by Falcorian on 2007-01-08
This depends on a few things:

Is your windows partition showing in Ubuntu? I mean, is it mounted?

If so, you can copy files from it to Ubuntu, but you can't write files to it (assuming it's NTSF).

If it's not showing up, you're going to have to mount it, which I can't really help with, since I'm horrible at figuring out mountings and whatnot. ;)


Windows probably won't  show your Ubuntu partition, but I've heard to can both get it recognized, and writable. But again, I'm not sure how exactly.


Hope that gives you a push in the right direction, and that others can answer your question fully!

---

### Post by scrooge_74 on 2007-01-08
First you need to mount the XP in linux so you can access the files there, but if the XP partition is NTFS you should not write anything back without first installing the correct programs for that. From XP you are going to install a similar program.

The easier way will be to have an intermediate partition in FAT32 so Linux and XP can each write to it

---

### Post by az on 2007-01-08
> **birdseye said:**
> How do I copy files from the windows partition to the linux partition and vice versa on a dual boot machine?

In windows, there is a driver for ext3.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

For NTFS, it used to be that linux could not write to NTFS because the NTFS filesystem is not documented.  That may soon change - there is a driver that has been reverse-engineered and may be eventually shipped with Ubuntu.

---

### Post by scrooge_74 on 2007-01-08
> **azz said:**
> In windows, there is a driver for ext3.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

For NTFS, it used to be that linux could not write to NTFS because the NTFS filesystem is not documented.  That may soon change - there is a driver that has been reverse-engineered and may be eventually shipped with Ubuntu.

I was wondering how long it wa going to take for you to come buy with the correct answer :D

---

### Post by luvinit on 2007-01-08
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by birdseye on 2007-01-08
Thanks. Ubuntu recognised the windows partition "out of the box" but it was read not write. So until I can get everything to work under Linux (struggling with Canon printer and PDA using gwenview) its a frustrating business of hopping from one system to another.

I'll have a go with the drivers suggested. Dont know whether I can alter the existing partitions to give a fat32 one - is there a limit on partition numbers? the partitioner in ubuntu seems to think it is 4.

---

### Post by scrooge_74 on 2007-01-08
Read this it could be usefull

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

this will give you an idea on how to proceed with making another partition since you have your system already working

---

