---
title: "[SOLVED] Dual partition help"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by wgn on 2007-12-09
I'm trying to install a dual boot on a Dell w/ XP.

Dell already has three partitions on the 60G HD (XP, DellRestore, DellUtilities).  I want to add three partitions for root, swap, and home but the partitioning tool in the installer will only let me make one more partition (doesn't matter whether its a primary or logical partition).  I've already resized the XP partition from 54G to 27G (haven't tried booting XP yet to see if I screwed that up).

What am I doing wrong?

---

### Post by wjp.reg on 2007-12-09
> **wgn said:**
> I'm trying to install a dual boot on a Dell w/ XP.

Dell already has three partitions on the 60G HD (XP, DellRestore, DellUtilities).  I want to add three partitions for root, swap, and home but the partitioning tool in the installer will only let me make one more partition (doesn't matter whether its a primary or logical partition).  I've already resized the XP partition from 54G to 27G (haven't tried booting XP yet to see if I screwed that up).

What am I doing wrong?

You can only have 4 primary partitions.  You need to create an extended partition and then create the logical parts within for your linux setup.

---

### Post by Eldar11 on 2007-12-09
you haven't done anything wrong, Windows just likes to make a whole bunch of partitions for nothing, but moving the files will cause problems when the programs can't find the files where they're supposed to.

you will only need two partitions open, one for the ext3 for the file system and one for swap.

just have the open space ready, when you install ubuntu, when it asks how you want to partition your disk, say use the free space on the disk. It should work and install, but if it gives you an error saying that you can only have 4 master partitions, you will need to get rid of one, and I'm not sure what you would do with the data.

---

### Post by wjp.reg on 2007-12-09
> **Eldar11 said:**
> you haven't done anything wrong, Windows just likes to make a whole bunch of partitions for nothing, but moving the files will cause problems when the programs can't find the files where they're supposed to.

you will only need two partitions open, one for the ext3 for the file system and one for swap.

just have the open space ready, when you install ubuntu, when it asks how you want to partition your disk, say use the free space on the disk. It should work and install, but if it gives you an error saying that you can only have 4 master partitions, you will need to get rid of one, and I'm not sure what you would do with the data.

Sounds like both of you should have a look at[ this]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html") article and anything else you can google about hard disk structures.

You definitely don't want to remove any existing partitions and there is no need to; if you shrink the primary windowsXP partition and create and extended partition, ubuntu will create a root and swap partition at installation. There is nothing wrong with not having a separate home partition unless you are planning to change linux distributions from time to time, and anyway, you can back the contents up; but that's for another forum search!

Good luck

---

### Post by wgn on 2007-12-09
I'd be happy to create an extended partition in the free space but that wasn't one of the options, only primary or logical.  How do I make an extended partition, and then subdivide it?

---

### Post by wjp.reg on 2007-12-09
> **wgn said:**
> I'd be happy to create an extended partition in the free space but that wasn't one of the options, only primary or logical.  How do I make an extended partition, and then subdivide it?

so choose logical..

---

### Post by wgn on 2007-12-09
I chose logical and mounted "/" as a 15G partition, but then the partitioning tool says the rest of the free space in unusable.

---

### Post by wjp.reg on 2007-12-09
Can you make due with a smaller root partition?  Swap sizes are about 1.5GBs for a 1GB RAM system.

---

### Post by wjp.reg on 2007-12-09
Once you get everything up and running you'll be able to get access to your windows partition for data access and storage.

---

### Post by wgn on 2007-12-09
The problem isn't too big a root partition (I think).  I've got a DellRestore partiton that's 4.6G, a DellUtilities partition that's 62.7M, and an XP (NTFS) partition that was 54G but I've resized to 25G.  That leaves 26G of unallocated space that I can only create a single new partition.  Don't I need at least 2 more partitions (for root and swap)?

---

### Post by thelatinist on 2007-12-09
Just delete that fourth partition, then run the installer and choose 'manual' on the Prepare Disk Space page and then the option to use largest free space.  The installer will create your extended partition and any logical partitions you need inside of it.

---

### Post by wjp.reg on 2007-12-09
> **thelatinist said:**
> Just delete that fourth partition, then run the installer and choose 'manual' on the Prepare Disk Space page and then the option to use largest free space.  The installer will create your extended partition and any logical partitions you need inside of it.

Thank you, that's what I have been saying, :lolflag:

---

### Post by wgn on 2007-12-09
OK, I'll give that a try.
Thanks for the help.  I'll let you know how it goes.

---

### Post by louieb on 2007-12-09
howdy wgn, please post your partition table. to do that 
boot to live cd and open applications>accessories>terminal  and key ```
sudo fdisk -l
``` (lowercase L) Without that or a GParted screen shot anything I could write would just be a guess.

---

### Post by thelatinist on 2007-12-09
> **wjp.reg said:**
> Thank you, that's what I have been saying, :lolflag:

I know!  People don't like easy solutions, I think.

---

### Post by uidb4056 on 2007-12-09
If you have resized the XP partition to got more free space, this free space will be between the XP partition and the other's partitions.
You will need that all primary partitions will be contiguous with the free space at the end to be able to create a fourth extended partition (you can't create an extended partition in a free space just before another primary partition). 

If you post the information of your partitions as Luieb asked in the previous answer will give light on it.

---

### Post by Jerry N on 2007-12-09
> **Eldar11 said:**
> ... Windows just likes to make a whole bunch of partitions for nothing.... 

I have made many XP installations and I have never seen Windows try to make multiple partitions unless I was trying to create a multiboot.  Companies like HP and Dell configure their systems with the system restore files in a hard drive partition because they are too cheap to include restore DVDs (and PC owners usually lose any disks that came with their computer anyway).  They may also install some of their "bloatware" in a separate partition.

Jerry

---

### Post by wgn on 2007-12-09
Eureka!  Everything is working.  Thanks for all the help.

I'll mark this as solved as soon as I figure out how.

---

