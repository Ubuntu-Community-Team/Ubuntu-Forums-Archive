---
title: "RePartitioning"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by nlbs on 2007-06-12
Previously I made a Dual Boot with Windows XP and Ubuntu
And Ubuntu 7.04 made a partion (5~6 GB) for It and Windows is installed in a Drive thats 20 GB
Now I wanna Move My Windows to 5 GB and My Ubuntu to 20 GB How can I do it without reformatting everything ??

---

### Post by dptxp on 2007-06-12
Maybe you post details of all your partitions first. Then we can see if there is a right way.

---

### Post by nlbs on 2007-06-12
This is the output of 
fdisk -l;


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

 Device   Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/sda2            2433        9729    58613152+   f  W95 Ext'd (LBA)
/dev/sda5            2433        3041     4891761    b  W95 FAT32
/dev/sda6            3042        3650     4891761    b  W95 FAT32
/dev/sda7            3651        5303    13277691    b  W95 FAT32
/dev/sda8            6083        7906    14651248+   b  W95 FAT32
/dev/sda9            7907        9729    14643216    b  W95 FAT32
/dev/sda10  *        5304        6042     5935986   83  Linux
/dev/sda11           6043        6082      321268+  82  Linux swap / Solaris


Partition table entries are not in disk order
```

---

### Post by nlbs on 2007-06-13
Hello Answer Please ??

---

### Post by dptxp on 2007-06-13
I think that you should use one of your fat32 partitions for data. You can format it in ext3 and make is /home. Then shift all data from home partition that is in root. Maybe it shall move when you make /home.

6 GB should suffice for Ubuntu (if no data is stored).

To make a separate home partition see the procedure here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome).

You can actually store data in other partitions Fat32 or EXt3 w/o making separate /home.

To reduce Window partition, defragment it (takes time), and then resize it.
To add the free space to next one, delete the next one so that you have the prev. free block
added and then reformat.

You shall need to mount new partitions

But backup important data first before playing with partitions.

---

### Post by tchoklat on 2007-06-13
use GPartEd on a CD as a live CD and use it to resize your partitions. You can not resize mounted partitiosn so you have to download GPartEd and burn the ISO to CD and use it. It is graphical and easy to use withacare!

---

