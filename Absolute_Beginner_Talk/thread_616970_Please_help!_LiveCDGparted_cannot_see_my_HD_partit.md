---
title: "Please help! LiveCD/Gparted cannot see my HD partitions"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by drinkmocha on 2007-11-18
I am dual-booting between XP and Ubuntu Gutsy. My Gutsy partition is completely broken (I can't see the GUI anymore, it shows me my files in a shell?!).

I am trying to format my Ubuntu by using the live CD, however, it only gives me the option to format the whole hard disk, which I don't want to do.. so no I can't reinstall Ubuntu :(

Here is what returns after typing fdisk (using system rescue CD, gparted here also does not see my partitions):

/dev/sda1 - (BLOCKS) 2618563 -  (SYSTEM) W95 FAT32 (LBA)
/dev/sda2 - (BLOCKS) 78493590 - (SYSTEM) HPFS/NTFS
/dev/sda3 - (BLOCKS) 74501437 - (SYSTEM) LINUX
/dev/sda4 - (BLOCKS) 3213000 - (SYSTEM) Extended
/dev/sda5- (BLOCKS) 3212968 -  - (SYSTEM) Linux Swap/ Solaris

I'm not sure how I ended having this partition list. However, PLEASE help. How can I reinstall ubuntu again safely without hurting XP?

THANKS!

* I have a Dell Vostro 1500 with 160 gb hard drive.

---

### Post by gcrussell1 on 2007-11-18
Can't you use fdisk to rework your partitions? If gparted doesn't see them but fdisk does, if seems like you should be able to use it to the same end. I had a similar problem with a friend's laptop, but I got it going after some juggling with fdisk and gparted. If you have a 2.5" enclosure or a SATA-USB connector, you might try running some partitioning utilities from a different computer with your hard drive connected externally - I think that was a key element in getting my friend's working.

I'd recommend using fdisk or the windows partition editor or something else to delete the linux partitions altogether (after saving any valuable info) and using gparted to reassign the free space that opens up. Now, getting those partitions deleted might be easier said than done, but if it can be done, you should be in the clear.

---

### Post by drinkmocha on 2007-11-18
Thanks for your reply. How do I do that using FDISK safely? I found somewhere in the net that I can do something like mkswap /dev/sda04... this is only for the swap, how about for the other ones?

---

### Post by drinkmocha on 2007-11-19
Anybody else have ideas? I wanna know if there's a way to fix the linux install so that the LIVE CD can recognize my partitions?

---

### Post by gcrussell1 on 2007-11-19
> **drinkmocha said:**
> Thanks for your reply. How do I do that using FDISK safely?

If you only use fdisk to delete the Linux partitions, it shouldn't affect the Windows side at all. You don't necessarily have to remake them, as long as you open up the space gparted should recognize the free space on the HD the next time you run it.

Of course, I'm not entirely sure how to do all of that with fdisk... I only played with it for a few minutes and that was a month ago. Maybe someone else can show you, or maybe you can search up a how-to or a site on using fdisk.

---

### Post by louieb on 2007-11-19
Sounds like your partition table is non standard.
Have you tried to install a distro that uses the **Disk Drake** partitioner such as PCLinuxOS? 

The reason I ask is that Disk Drake can arrange partitions in a manner that  Gparted cannot handle.
Please post the output of```
 sudo fdisk -l
``` (lower case L)

---

### Post by steve.horsley on 2007-11-19
I would be inclined to use either fdisk or cfdisk to delete partitions sda5, sda4 and sda3 (in that order), and then run the installer again, telling it to use the free disk space. It shoudl then recreate and reformat those partitions. This avoids the rather messy custom partition dialog that you have to use when instaling onto existing partitions.

P.S. I guess that sda2 is your Windows partiton, and sda1 is a manufacturers utility/restore partition.

---

