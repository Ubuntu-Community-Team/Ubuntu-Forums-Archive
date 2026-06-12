---
title: "just another boring install question"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-01-20
Hi folks! This is my setup. -PC with 3 partitions . 1. Xp (primary) 2. Data ntfs. (ntfs) 3. Primary (fat).I would like to install Ubuntu 5.10 on to the 3rd partition (20GB). I now have the CD to do this. How do I proceed from this point. (Holding hands through this procedure? - Yeah!)
Thanks for any info.

---

### Post by aysiu on 2006-01-20
Installing Ubuntu to FAT isn't a good idea.
How about this instead?

1. XP NTFS
2. Data FAT
3. Ubuntu Ext3

---

### Post by dueY on 2006-01-20
Like aysiu said you should install Ubuntu to an ext3 partition.  His setup has the advantage of having a data drive that can r/w/e from both Windows and Ubuntu since it is FAT32.

---

### Post by Sbarton on 2006-01-20
aysiu, sounds great but on install of disc how or what do I change to proceed? thanks!

---

### Post by soonindallas on 2006-01-20
ubuntu will not live on fat.

recover anything you need from that partition.

insert the install cd.

follow the install process onscreen. the process will ask what you want to to with your disk.

you will need to make at least 2 partitions for ubuntu: system + swap is a minimum.  you might want to make a 3rd partition for /home (your confing and files).  I wish I had when I installed ubuntu a year ago.

---

### Post by dueY on 2006-01-20
[QUOTE=soonindallas]ubuntu will not live on fat.

recover anything you need from that partition.

insert the install cd.

follow the install process onscreen. the process will ask what you want to to with your disk.

you will need to make at least 2 partitions for ubuntu: system + swap is a minimum.  you might want to make a 3rd partition for /home (your confing and files).  I wish I had when I installed ubuntu a year ago.[/QUOTE]

Technically you don't NEED the swap.  It's just recommended.

---

### Post by aysiu on 2006-01-20
[QUOTE=Sbarton]aysiu, sounds great but on install of disc how or what do I change to proceed? thanks![/QUOTE] See the fifth link of my signature. It tells you everything... and with screenshots!

---

### Post by GreyFox503 on 2006-01-20
The Ubuntu partitioner is not too hard to work with.  The gist of what you need to do is this:

From within the installer, delete the 3rd partition (the 20GB FAT one).  That will erase all data on the partition so make sure you back it up.  Then just tell Ubuntu to work its automagic on the free space, and it should make an appropriate / and swap partition.

If you want a separate /home partition, now is the time to make it.  If you don't know what a /home partition is, then I would just leave it alone as it will simplify your install.

---

