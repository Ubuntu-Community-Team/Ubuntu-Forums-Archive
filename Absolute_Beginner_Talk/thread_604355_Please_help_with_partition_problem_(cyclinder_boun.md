---
title: "Please help with partition problem (cyclinder boundary)"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by madu on 2007-11-06
Hi guys...

This one of the major problems I'm having after upgrading to Gusty... and unfortunately I cant re-install Fiesty because this error keeps the installer from seeing partitions... installer only sees the hdd.. no partition... and I'm in a very diabolical position becasue I need to get out of Gusty.. my network is not working and there are logical disk I/O errors.. I dont want to fix Gusty.. just wanna go back to Fiesty... the only way to install in this manner is to re-partition the whole drive and its gonna wipe off my XP and recovery partitions.. and I cant afford to do that.. so you see I'm stuck with a partially functioning Gusty and XP (which I dont wanna go back to :().. 

Here are some command outputs..

> :~# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc78e21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         668     5360640   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         669        2603    15535800    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            2603        6250    29295000   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            6250       14593    67019400    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5   ?        6250      273599  2147483647+  ff  BBT
/dev/sda6            6493       10317    30716248+   7  HPFS/NTFS
/dev/sda7           10317       12229    15361888+   7  HPFS/NTFS

>  :~# fdisk /dev/sda

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
omitting empty partition (5)

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.


Expert command (m for help): v
Partition 1 does not end on cylinder boundary.
Partition 2 does not end on cylinder boundary.
Partition 3 does not end on cylinder boundary.
Partition 5: head 256 greater than maximum 255
Warning: partition 5 overlaps partition 6.
Warning: partition 5 overlaps partition 7.
Logical partition 5 not entirely in partition 4
134058763 unallocated sectors

Expert command (m for help): q
  

and also before Ubuntu starts up I get about 10 lines of "Logical I/O error in /dev/sda5..."

Any help would be greatly appreciated...

Madu...

---

### Post by P4man on 2007-11-06
Woha, that is a lot of partitions. Not sure that is your problem, but I thought Linux only supported 4 primary partitions per disk max. Could that have anything to do with it ?

---

### Post by madu on 2007-11-06
No idea about that man..Just have my recovery partition, XP partition and twp more extended partitions in XP...
But I had absolutely ZERO partition problems with Fiesty..

---

### Post by frodon on 2007-11-06
You should check your disk first running a "fsck -a" on it, the easiest way to do this is to use a live CD.
Your disk may have a problem so it is the first thing to check IMO.

---

### Post by madu on 2007-11-06
thanks man.. will try that out...

---

