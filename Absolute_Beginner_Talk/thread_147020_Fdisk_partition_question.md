---
title: "Fdisk partition question"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-19
Below is one of my drives (didn't include the other drive since I have no questions about it).  This drive has 4 partitions. 

NTFS with the XP OS on it.
Fat32 with applications/games for windows and data
Ubuntu OS
Swap 

Yet 5 are listed below.  I'm just curious as to what the extra one is?

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hda2            6375       14945    68846557+   f  W95 Ext'd (LBA)
/dev/hda5           11474       14945    27888808+   b  W95 FAT32
/dev/hda6            6375       11237    39061984+  83  Linux
/dev/hda7           11238       11473     1895638+  82  Linux swap / Solaris

---

### Post by Steve1961 on 2006-03-19
[QUOTE=Kersus]Below is one of my drives (didn't include the other drive since I have no questions about it).  This drive has 4 partitions. 

NTFS with the XP OS on it.
Fat32 with applications/games for windows and data
Ubuntu OS
Swap 

Yet 5 are listed below.  I'm just curious as to what the extra one is?

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hda2            6375       14945    68846557+   f  W95 Ext'd (LBA)
/dev/hda5           11474       14945    27888808+   b  W95 FAT32
/dev/hda6            6375       11237    39061984+  83  Linux
/dev/hda7           11238       11473     1895638+  82  Linux swap / Solaris[/QUOTE]


/dev/hda2 is an extended partition that contains the logical partitions /dev/hda6, /dev/hda7 and /dev/hda5.  So you have one primary partition - hda1 - and three logical partitions within an extended partition.  Basically whenever you create a logical partition you also create an extended partition, so nothing to worry about.

---

