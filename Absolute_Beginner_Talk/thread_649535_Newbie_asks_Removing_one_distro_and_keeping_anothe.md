---
title: "Newbie asks: Removing one distro and keeping another?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by vasa1 on 2007-12-25
Hi All:

Newbie question:

I have WinXp (without the installation disks (;-) and then installed OpenSUSE 10.3 (so dual boot). I then installed Ubuntu 7.10 (so "triple" boot). I have both these install disks.
 
Can I "uninstall OpenSUSE 10.3" leaving WinXP and Ubuntu intact and functional. Is that a hazardous thing to do? Any FAQs, how-tos, etc.?


Add: I have only one hard disk (160 GB), partitioned by WinXP into C, E, F, and G drives as NTFS.

The two Linux distros did their own thing (i.e., ext 3 formatted part of the C drive, I think). 

I can't be sure because Windows XP doesn't show the ext3 parts.


Thanks for your time.

AE Souza

---

### Post by PmDematagoda on 2007-12-25
You can format the OpenSUSE partition and then use it as separate partition or you can delete it and resize the Ubuntu partition to include the previous OpenSUSE one. You can do all that using Gparted which can be installed by executing:-

```
sudo apt-get install gparted
```
Gparted can then be found in System>Administration>Partition Editor.

But as a precaution, download and burn [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download") to a CD so that it can be used in case of a GRUB failure.

---

### Post by Flyingjester on 2007-12-25
+1 for gparted it's an excellent program and should take care of your needs, also the advice about supergrub is sound.

---

### Post by hermitical on 2008-04-28
I'm in a similar situation but only have Ubuntu and Opensuse on my laptop (inadvertently ditched Vista!)

Looking at G-part I have 4 partitions
sda1 - linuxswap
sda2 - ext3 /media/sda2        boot
sda3 - ext4
sda4 - ext3 /media/sda3

sda2 is my opensuse partition and is flagged as boot but I want to get rid of it. Am I ok to go ahead and delete then resize or should I do something else first?

---

### Post by PmDematagoda on 2008-04-28
hermitical please don't resurrect such an old thread to give your problem, you would have done better had you given the problem in a new thread of your own with the full explanation of your problem/s.

This thread is closed.

---

