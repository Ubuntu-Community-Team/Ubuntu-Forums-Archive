---
title: "which is boot disk"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by sandysandy on 2007-11-07
hi guys

I have Ubuntu 7.10 installed on two hard disks, in addition to Win XP (2 partitions) and Mandriva.
[COLOR="Red"]i want to know which all partitions are bootable[/COLOR]. i am able to boot one ubuntu and both XP. my mandriva install which was working ok is now booting into ubuntu.

system specs Pentium D 3.0 GHz, 1GB RAM, 160Hdd SATA hdd ( WinXP - 2 partitions, Ubuntu 7.10, Mandriva), 40Gb IDE Hdd (Ubuntu 7.10). Booting sequence is 40GB hdd first.

The output of [COLOR="Red"]sudo fdisk -lu[/COLOR] is as follows:-


[COLOR="Blue"]Disk /dev/sda: 40.0 GB, 40020664320 bytes[/COLOR]
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x40634062

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris
[COLOR="Blue"]
Disk /dev/sdb: 160.0 GB, 160041885696 bytes[/COLOR]
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe138e138

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sdb2        51199155   266373764   107587305    f  W95 Ext'd (LBA)
/dev/sdb3       266373765   312560639    23093437+   7  HPFS/NTFS
/dev/sdb5        51199218   133114589    40957686    7  HPFS/NTFS
/dev/sdb6       215030088   221327504     3148708+   7  HPFS/NTFS
/dev/sdb7       264285378   266373764     1044193+   7  HPFS/NTFS
/dev/sdb8       221327568   229504589     4088511   82  Linux swap / Solaris
/dev/sdb9       229504653   238131494     4313421   83  Linux
/dev/sdb10      238131558   247224284     4546363+  83  Linux
/dev/sdb11      247224348   261136574     6956113+  83  Linux
/dev/sdb12      261136638   264285314     1574338+  82  Linux swap / Solaris
/dev/sdb13      133114653   156440969    11663158+  83  Linux
/dev/sdb14      156441033   166208489     4883728+  83  Linux
/dev/sdb15      166208553   175976009     4883728+  83  Linux

Partition table entries are not in disk order

regards

---

### Post by WorldTripping on 2007-11-07
If I remember rightly, the partitions with the '*' are bootable.

i.e. the;

/dev/sda1 *
/dev/sdb1 *

I think this was new with Gutsy, as I don't remember it before.

You might want to verify what I said, as I'm not at my machine at the moment, and can't check.

---

### Post by sandysandy on 2007-11-07
even i thought so, but the * is only in front of 

/dev/sda1 * 63 74862899 37431418+ 83 Linux

/dev/sdb1 * 63 51199154 25599546 7 HPFS/NTFS

where as i am presently booted into

[COLOR="Blue"]/dev/sdb15 [/COLOR]166208553 175976009 4883728+ 83 Linux

which does not have a * sign

regards

---

### Post by WorldTripping on 2007-11-07
You could use cfdisk.

> sudo cfdisk /dev/sda

cfdisk is a partition manager, but it does tell you which partitions are marked as bootable.

## caveat - cfdisk is powerful, use with caution. ##

---

### Post by sandysandy on 2007-11-07
thanks

it lists only the disks identified by u earlier as bootable 

/dev/sda1 *
/dev/sdb1 *


how do i set boot flag to other partitions sdb 15. also is it possible to find out which partition has my mandriva system so that i can set boot flag to it.

regards

---

### Post by WorldTripping on 2007-11-07
Sorry,

Both of those questions are out of my knowledge sphere at this point in my Linux life.

Someone else might be able to help you.

Apologies.

---

### Post by sandysandy on 2007-11-07
thanx for all the help

regards

---

### Post by sandysandy on 2007-11-07
is it possible to have more than one partitions as active or boot.

i am having to force boot ubuntu using SGD. is there any way i can set the boot flag to ubuntu partition so that it boots automatically. i don't want to rewrite GRUB to MBR unless necessary as with great difficulty i have retrieved my MBR.

thanks

---

### Post by crf on 2007-11-07
Try reading this manual. It's pretty good.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

I don't think the bootable flag matters.

You can write a grub configuration file, telling it where both your linuxes are, and copying it to the MBR.

---

