---
title: "I want to delete partition of harddrive"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Alpha.9 on 2007-12-30
Hi, 

I have installed XUBUNTO 7.10 on my old computer. With the installation I wanted to delete the old partition of the HD (it has only 8.5 GB), but xubunto refused to do so. I finaly came up with the following partitions:

------------------------------------------------------------------------------
Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001f446

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         345     2771181   82  Linux swap / Solaris
/dev/sda2             945        1027      666697+   5  Extended
/dev/sda3   *         346         944     4811467+  83  Linux
/dev/sda5             979        1027      393561   82  Linux swap / Solaris
/dev/sda6             945         978      273042   82  Linux swap / Solaris

Partition table entries are not in disk order
------------------------------------------------------------------------------

Unfortunately, running xubunto means that I have only 4.5 GB space on my hd. I lost app. 4 GB which I want to get back. 

Does anybodey has an idea how to delete the partitions? I only want one partition with the 8.5 GB. 

I already tried a new installation of xubunto, but it didn't work.

Thanks in advance for your help.

---

### Post by jken146 on 2007-12-30
Which partition do you want to delete?  And why do you have so many swap partitions?

---

### Post by Paqman on 2007-12-30
Are you using Gparted to modify/delete the partitions? You can get it on a [LiveCD](http://gparted-livecd.tuxfamily.org/), which is very handy. You can't normally modify partitions that are mounted. Using the LiveCD none of your partitions are mounted, so you can delete/resize/move them at will.

In your case, you can delete all the unwanted paritions and grow your main partition to fill the space created. You'll want to keep a swap partition, too.

---

