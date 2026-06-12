---
title: "Media Direct Button Corrupted My Partitions"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by rocketscientistnot on 2007-09-28
I had been running my Inspiron 1505 with dual boot of XP and Ubuntu.  During the setup of my dual boot, I wiped out my hard drive and had to reinstall XP.   I recently hit the Media Direct button instead of the Power button.  Since then I have not been able to boot into XP.  If I select XP from grub, it starts to boot.  Then I get a blue screen with a STOP: 0x000000CA error.  In reading from these forums I have learned that Media Direct messes with the MBR.  I can still boot to Ubuntu, and I can even "see" the partition containing all of my windows files.

I've done a fdisk-l and got: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           13714       13974     2096451    c  W95 FAT32 (LBA)
/dev/sda2   *           7        2556    20482875    7  HPFS/NTFS
/dev/sda3            6690       13974    58516762+   f  W95 Ext'd (LBA)
/dev/sda4           13975       14593     4972117+  db  CP/M / CTOS / ...
/dev/sda5           13714       13974     2096451   dd  Unknown
/dev/sda6            6690        9239    20482812   83  Linux
/dev/sda7            9240        9506     2144646   82  Linux swap / Solaris
/dev/sda8            9507       13713    33792696    b  W95 FAT32

Partition table entries are not in disk order

I appear to have overlapping partitions, and gparted now shows everything as gray, unallocated space.  

Can I fix this?  Do I just need to reformat and start over?  Any advice?

---

### Post by jordoex on 2007-10-01
I need help with a similar problem!!!

---

### Post by rocketscientistnot on 2007-10-05
I managed to fix this! I followed advice from these forums and re-installed grub.  But that didn't fix my problem.  I was close to formatting my drive and starting all over, when I decided to hit the Media Direct button again.  The Media Direct started up and I was able to boot into XP.  Once I exited normally out of XP, all was well.  I went back into Ubuntu and found that Gparted could now see my previously "unallocated" hard-drive again.  It's worth a try.

---

### Post by jordoex on 2007-10-09
My problem was only with Gparted not seeing my disks... I fixed it by running an old version of Partition Magic and a couple of other utilites and it seemed to work.

---

