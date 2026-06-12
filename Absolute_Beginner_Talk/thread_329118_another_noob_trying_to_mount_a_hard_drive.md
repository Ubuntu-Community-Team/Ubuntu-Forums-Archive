---
title: "another noob trying to mount a hard drive"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by SaltyTaro on 2007-01-01
is what i am.  i had read the instructions on how to mount before, using the terminal, making a place to mount to, finding the location of the drive, and changing the fstab.  the directions are very straightforward
so here was my fdisk -l
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdc5               2       24321   195350368+   7  HPFS/NTFS

Disk /dev/sdd: 521 MB, 521142272 bytes
32 heads, 32 sectors/track, 994 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         994      508911+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(992, 31, 32) logical=(993, 31, 31)

the two 200 gigabyte ones are the ones i'm trying to get to, so they're at /dev/sdb1 and /dev/sdc5, right?  so here comes the fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7735bc62-b40a-402d-8db9-ca16a8eb5e17 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6ea1d92f-0285-4382-93f9-deb0cd5f5cdd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

no sdb1 or sdc5 in sight.  what am i doing wrong?

---

### Post by meng on 2007-01-01
Well you clearly haven't edited your fstab (not in a way that the changes "stuck" at any rate). Perhaps you opened the file without superuser privileges, and therefore could not write the changes. Or perhaps you didn't edit /etc/fstab at all.

I'm going to assume you know what you are supposed to do with your fstab, so then go ahead and:
sudo vim /etc/fstab
or
sudo nano /etc/fstab
or
gksu gedit /etc/fstab
(or invoke your favorite editor if it's none of these)

---

### Post by SaltyTaro on 2007-01-01
i know how you're supposed to edit the fstab.  but in the tutorial, it tells you to find the line in fstab that has the hard drive you want to mount so there should be a line for sdb1 and sdc5 for me to edit, but the problem is that it doesn't even come out for me.  should i make a brand new line?

---

### Post by meng on 2007-01-01
Yes.
You create a new line, what I would suggest is:
dev/sdb1       /media/windows  ntfs    nls=utf8,fmask=0333,dmask=0222   0       0
(replace /media/windows with wherever you want to mount TO)
the number of whitespaces is not important.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by SaltyTaro on 2007-01-01
ah, that sounds good, thanks for the fast reply :KS

---

### Post by Naturally on 2007-01-01
I am an Ubuntu newbie my self. 

I used [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) to mount my NTFS and FAT32 drives to extremely good results.

I found that tutorial straight to the point and very easy to follow and successfully monuted all the partitions that I wanted. Good luck. I am begining to find out that Ubuntu is worth the trouble.

---

