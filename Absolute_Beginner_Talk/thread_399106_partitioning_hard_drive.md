---
title: "partitioning hard drive"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by royal314 on 2007-04-01
another noob question: I just installed ubuntu to dual-boot on my computer a few days ago and i only used 3 partions, 30 gb ext3, 2gb linux-swap, leavung aboud 100 gb for windows ntfs, is there a way to use some of this ntfs partition and create a fat32 shared partition?

---

### Post by kahrytan on 2007-04-01
You can read/write to a ntfs partition. Read the [NTFS Howto here]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+howto").

---

### Post by royal314 on 2007-04-01
this is the first i've heard about this, has anyone here done this?
also i think i would rather have a separate partition for shared flies if possible.

---

### Post by antoz on 2007-04-01
If you have the live CD boot from the cd and then use Gparted to rezise your window ntfs partition and then create a fat32 in the empty space. It is good to defrag your windows drive first before you begin.
It is pretty straight forward once you rezised your window partition just right click on the unlalocated space and create your new partition.A

---

### Post by royal314 on 2007-04-01
boot from the live cd and then click install to run gparted?

---

### Post by esodin on 2007-04-01
> **royal314 said:**
> this is the first i've heard about this, has anyone here done this?
also i think i would rather have a separate partition for shared flies if possible.

I have 4 physical drives in my PC 2 are single partitions while 2 have 2 or 3 partitions. Most of them (except for the Linux partitions) are NTFS (no FAT32) drives. It works very well I can access all the drives and partitions from linux.

Under Edgy, if you get NTFS-3G using Automatix2, Automatix will set up the mounting procedure (at start up) for you. If you have Feisty installed it is automatic once NTFS-3G is installed.

:)

---

### Post by Maestro23 on 2007-04-01
> **royal314 said:**
> boot from the live cd and then click install to run gparted?

..

---

### Post by ahaurw01 on 2007-04-01
> **royal314 said:**
> this is the first i've heard about this, has anyone here done this?
also i think i would rather have a separate partition for shared flies if possible.

Royal, you may have read different places that mounting ntfs partitions read/write with linux could be a potentially dangerous situation, but just to reiterate, I use ntfs-3g to mount an external drive plus my windows partition (I dual boot XP) both read/write and I've never had any problems whatsoever. 
Happy ubuntuing!

ps I'd also really recommend backing up any important stuff before doing any sort of resizing or partitioning. Even though it is supposed to work without problems, ya know, something could always come up widway through to cause a partition to be wiped.

---

### Post by antoz on 2007-04-01
To access g parted click on System then Administration

---

### Post by zvacet on 2007-04-02
Defragment ntfs few times before you resize it.Resize it  and make fat32 with
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

