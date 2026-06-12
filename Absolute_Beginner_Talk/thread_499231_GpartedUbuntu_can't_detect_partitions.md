---
title: "Gparted/Ubuntu can't detect partitions"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Tomshaq on 2007-07-12
Hi,

I run ubuntu at home, and I recently converted my sister to have her try out a dual boot.
She has a dell inspiron 1505 running xp and I am trying to install feisty on it.

So, this computer has ridiculous partitions on it, it already had 4 when I started messing around with it. So I cleared one using the partitioner in the ubuntu install and create an extended partition for the ubuntu install. First of all, is it a problem to try to install feisty on an extended partition? In order to create a swap or /home, I need to make it an extended partition, because I don't want to clobber the 'dell utility' or backup partition.

Anyways, my real issue is that after reformatting to ext3, the partitioner couldn't create a separate swap partition, so I unmounted and mounted the partition, but with no success. I got frustrated with the ubuntu liveCD, and booted into my liveCD of Gparted to finish up the partitioning, but no partitions are detected. It only detects one big unpartitioned hard drive.
I put ubuntu back in, and it can't detect any partitions either. I'm thinking 'oh crap I just hosed this hard drive' , but when I boot to windows, everything seems alright. Any ideas what is causing this?

---

### Post by Inxsible on 2007-07-12
I am not sure why its showing up as a huge unallocated drive, but you can surely install Ubuntu in an extended partition. I currently have Vista in a primary partition and /,/home and swap in an extended partition. I also have two other primary partitions one each for Linux and Windows.

Sorry cant be of any more help. Maybe if you try the LiveCD again ?

---

### Post by gameman12 on 2007-07-12
sounds wierd...just to clarify, did u have any periphrials attatched to the computer when u booted into gparted. like a digital camera or external hdd.

---

### Post by Tomshaq on 2007-07-12
No, nothing else is attached to the computer, and I've never seen a problem like this before, and I've installed ubuntu including partitioning 4 times before this.


Any thoughts?

---

### Post by bren on 2007-07-12
yep i have seen this before

its just my guess but i think this is down to a corrupted partition table

the good news is you can fix it

google for "systemrescuecd" and find the one (there are several) which includes utility testdisk

burn the iso and boot from the cd

right click desktop and choose testdisk

analyse and check the current partition table (sometimes you don't have to change anything)

save and exit (and it writes the new partition table)

voila
bon courage

bren

---

### Post by Tomshaq on 2007-07-12
Alright, I will try that out tonight and hopefully convince my sister to let me at her laptop again.

muchas gracias,

Tomshaq

---

### Post by Big_Croc7 on 2007-07-12
You can also get testdisk from the feisty repos - saves you using another CD :-)
It's in universe I think - it's only 1Mb or so, so you can easily get it while running the liveCD.

---

### Post by Tomshaq on 2007-07-12
Alright, I might try it by downloading from the repos. I already made the systemcd thing, but it at least seems pretty useful, if nothing else, it is another livecd with gparted, and there are not enough of those in the world. anyways, cds are dirt cheap nowadays :)

---

