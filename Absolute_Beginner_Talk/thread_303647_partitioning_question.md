---
title: "partitioning question"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by smile_sunshine on 2006-11-20
Hi,

I have xubuntu installed currently on hda3, and want to increase the partition size so that it takes up the whole of the first hard disk except the swap partition - (ie hda1, hda2 and hda3). 
I know its a problem with adding space to the start of the partition - is there any way to do this - or copy everything and move it? or do i have to reinstall and lose all my settings??

heres the output of   sudo fdisk -l
thanks :) 



Disk /dev/hda: 15.3 GB, 15361597440 bytes
240 heads, 63 sectors/track, 1984 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         388     2933248+  83  Linux
/dev/hda2             389         712     2449440   83  Linux
/dev/hda3             713        1900     8981280   83  Linux
/dev/hda4            1901        1984      635040   82  Linux swap / Solaris

Disk /dev/hdb: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         243     1951866   83  Linux
/dev/hdb2             244         486     1951897+  83  Linux
/dev/hdb3             487        1580     8787555    b  W95 FAT32
/dev/hdb4            1581        1653      586372+  82  Linux swap / Solaris

---

### Post by steve.horsley on 2006-11-20
gparted shoud be able to do the business for you, but you won't be able to resize the partition while running from it. You will have to use a live CD. I really don't know if gparted will also modify the filesystem to know that the partition is bigger. If it doesn't, then I guess you will have to copy the data off, re-format with mkfs, and then copy the data back - tar is good for doing that.

I suggest that you consider having separate system and home partitions so you can reinstall or upgrade your system without losing all your data. In fact I keep 2 system partitions, one for a trusted system and one for a trial upgrade. Once I'm happy with the next release, I start using that full time and eventually replace th eold one with the next release again. I'm currently on Dapper and Edgy - haven't been back to Edgy for a few weeks.

---

### Post by sgstarling on 2006-11-20
Hey Steve, I REALLY like your idea.

Let me see if I understand though. You in essense have 3 partitions:

1. Dapper
2. Edgy
3. Home/user

Is that right? How many GB do you set aside for the 'system' partitions? (1 and 2 above)

Can you give any more tips or ideas on how a newbie like me can set this up?

---

### Post by bodhi.zazen on 2006-11-20
> **sgstarling said:**
> Hey Steve, I REALLY like your idea.

Let me see if I understand though. You in essense have 3 partitions:

1. Dapper
2. Edgy
3. Home/user

Is that right? How many GB do you set aside for the 'system' partitions? (1 and 2 above)

Can you give any more tips or ideas on how a newbie like me can set this up?

Partition with Gparted or fdisk.

Each root partition should be 10-15 Gb, although you could go as small as 5 Gb if needed.

[This thread](http://ubuntuforums.org/showthread.php?t=300246) has a nice discussion of /home as well.

---

### Post by steve.horsley on 2006-11-22
Correction - I haven't been back to **Dapper** for several weeks - I'm Edgy full time now.

On my laptop, it's 5 Gig each for Dapper, Edgy and /home partitions - that's all the space I have.

My desktop is 20G for the systems (allows room for ut2004 and doom3 in /opt) and 50G for /home, but I also have around 100G unused/un-partitioned as yet.

---

