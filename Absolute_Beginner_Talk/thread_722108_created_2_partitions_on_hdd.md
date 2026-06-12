---
title: "created 2 partitions on hdd"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by catroaring on 2008-03-12
OK, i installed ubuntu on hdd(using the full hdd).  i broke the gui, only got cmnd line after that.  so i reinstalled ubuntu and partitioned the hdd 50/50(i want to try fedora 8 on the other partition).  i now have a partition running gutsy fine, and a broken fiesty.  how do i delete the fiesty, but keep the boot loader, which i asume is on the fiesty partition?

cr

---

### Post by housam on 2008-03-12
The latest installation is takeing the grub lead. so, if you installed Gutsy after feisty there is no problem to delete feisty. but also installing fedora will take the grub lead.
and Don't forget to create a swap partition.

---

### Post by catroaring on 2008-03-12
and how do i delete if even needed the fiesty partition.  and how do i create a swap partition?

---

### Post by housam on 2008-03-12
> **catroaring said:**
> and how do i delete if even needed the fiesty partition.  and how do i create a swap partition?

download the [[COLOR="Red"]_Gparted tool _[/COLOR]]("http://gparted-livecd.tuxfamily.org/")and burn it to a cd. then boot from it and you will see all the partitions. point to it and click to delete. this will leave an unallocated space that you can use it to create two new partitions. one to install fedora on it ( ext  format )and the other one is the swap ( 1 GB is ok ).

but I wonder about not having a swap partition fpr Gutsy ??. It may use the other partition( feisty ) as a swap . and that means if you delete it , Gutsy will not work.

before doing any thing type in a terminal 
```
sudo fdisk -l
``` 
where -l is a small L and post the results.

---

### Post by catroaring on 2008-03-12
human@athlon1800:~$ sudo fdisk -l
[sudo] password for human:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x220a5000

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       10225    82132281   83  Linux
/dev/hda2           18988       19457     3775275    5  Extended
/dev/hda3   *       10226       18987    70380765   83  Linux
/dev/hda5           19223       19457     1887606   82  Linux swap / Solaris
/dev/hda6           18988       19222     1887574+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2cb3844

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14945   120045681    7  HPFS/NTFS

Disk /dev/sda: 20.0 GB, 20000267776 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    0  Empty
/dev/sda2               6        2431    19486845    b  W95 FAT32

---

### Post by housam on 2008-03-12
I see that you have 3 HDD's . at  the first one with 160 GB you already have 2 swap partitions so, you don't need to create any more of them.
and you have also 2 ext3 partitions (feisty & Gutsy ) and one of them  has the boot mark (*) which is Gutsy.( be sure of that by noticing that in the grub menu at restarting - Gutsy should be on hda3 ).
if so, you can only reformat hda1 using Gparted tool.

---

