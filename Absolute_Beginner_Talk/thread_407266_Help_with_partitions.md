---
title: "Help with partitions"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by frankie0 on 2007-04-11
Hi, I just installed Ubuntu 6.10 on my computer with XP. I made the FAT32 system to share with XP and Ubuntu, but Ubuntu doesn't show it anywhere. It only shows my XP drive which is NTFS, but not my FAT32 system:confused: . How do I make Ubuntu recognize it?. Any help is appreciated.

---

### Post by darkrose on 2007-04-11
It is most likely there, but just not mounted.
Open a terminal, and provide the output of these 2 commands:

sudo fdisk -l
mount

That's a lowercase L on the first command, which will list all your hard drive partitions.
The second command will tell us what is currently mounted.

---

### Post by tarek on 2007-04-11
I just posted a solution for the same problem, go to [http://ubuntuforums.org/showthread.php?t=407180&page=2](http://ubuntuforums.org/showthread.php?t=407180&page=2)

tarek

---

### Post by frankie0 on 2007-04-12
Hey I just found out that my FAT32 has been mounted this entire time!! I thought it would show up as a hard drive, but I found out that it was just a folder. Now I can share between XP and Ubuntu. Thanks for the help anyway!:D

---

