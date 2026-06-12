---
title: "Ubuntu on a logical drive (planning out partitions)"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Ophidian on 2007-06-29
Hello! My hard drive has two partitions--one for WinXP, and one logical partition of 47.6 GB (in NTFS format right now) that I'd like to divide up to make my Dell Inspiron e1505 dual boot between WinXP and Ubuntu. 

First, I'd like to share a partition for both WinXP and Ubuntu for files -- which format should I make this partition (FAT32, ...? ) 

Second, what will I need to do while going through the installation process? I mean, what sizes does the OS and swap need? I'm honestly new to dividing a partition from scratch.

---

### Post by starcraft.man on 2007-06-29
> **Ophidian said:**
> Hello! My hard drive has two partitions--one for WinXP, and one logical partition of 47.6 GB (in NTFS format right now) that I'd like to divide up to make my Dell Inspiron e1505 dual boot between WinXP and Ubuntu. 

First, I'd like to share a partition for both WinXP and Ubuntu for files -- which format should I make this partition (FAT32, ...? ) 


Yup, Fat32 works fine for storage in Linux and Windows. If your planning on writing to the drive very often, you might wanna go for NTFS and the ntfs-3g drivers (search forums for how to). NTFS is journaled and has other advantages over Fat32 for frequently written to drives.

> Second, what will I need to do while going through the installation process? I mean, what sizes does the OS and swap need? I'm honestly new to dividing a partition from scratch.

Root filesystem requires a base of only 4-5 GB. I recommend 8 GB which gives you plenty of expansion room. As for swap, my rule of thumb is if you have 2 GB or less you should have 1 GB swap. If you have 3 or more GB of ram, 256 is more than enough (Ubuntu isn't a resource hog like Vista :))

Since your planning on a shared partition for XP and Linux I won't bother recommending a separate home partition.

---

### Post by Ophidian on 2007-06-29
> **starcraft.man said:**
> Yup, Fat32 works fine for storage in Linux and Windows. If your planning on writing to the drive very often, you might wanna go for NTFS and the ntfs-3g drivers (search forums for how to). NTFS is journaled and has other advantages over Fat32 for frequently written to drives.


Are there any disadvantages to keeping the partition at Fat32? I suppose I'll write to the partition at least once on a daily basis.

---

### Post by starcraft.man on 2007-06-29
> **Ophidian said:**
> Are there any disadvantages to keeping the partition at Fat32? I suppose I'll write to the partition at least once on a daily basis.

Like I said, Fat32 doesn't have the journaling of NTFS (its complicated, if you don't know best to search wiki for an explaination on file system journaling), it fragments faster than NTFS and it also has a maximum file limit (maximum size of a single file, i.e. one giant blog of data like an ISO) of 4 GB I believe. On the plus, it is natively supported (no need to install drivers) and if you use it for long term storage of files less than 4 GB it doesn't pose any problem.

NTFS partition requires ntfs-3g drivers, they are very stable from what I heard though. It will of course have journaling, support files much larger than 4 GB and fragments less easily.

Your choice. Wikipedia both and you'll see. NTFS is the superior FS of the two, long as you don't mind installing the ntfs drivers as an extra step.

---

