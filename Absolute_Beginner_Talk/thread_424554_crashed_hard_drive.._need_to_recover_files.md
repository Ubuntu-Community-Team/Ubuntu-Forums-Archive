---
title: "crashed hard drive.. need to recover files"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by BillGod on 2007-04-26
My hard drive just took a crap.  freakin brand new 320gb western dig!  I ran the wddiags tool. It found errors and asked if I wanted to run extended test.. I said yes.  Now whole file system is gone.  This is my \home drive.  Everything is on it.  ext3 partition.  Is there any recovery tools for ubuntu.  I know 1000 for windows.  Do not know any for ubuntu though.  Any thoughts and Ideas would be great.  I ran fdisk and printed table.  nothing there.

---

### Post by BillGod on 2007-04-26
ok i take that back.. fdisk shows this.


Command (m for help): p

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux


If I try and mount i get this

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: special device /dev/sda1 does not exist

---

