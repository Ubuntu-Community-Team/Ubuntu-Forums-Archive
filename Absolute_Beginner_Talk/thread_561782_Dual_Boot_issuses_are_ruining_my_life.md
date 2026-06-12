---
title: "Dual Boot issuses are ruining my life"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by CptnFantasy on 2007-09-28
I'm a total Ubuntu noob, so bear with me.

Last week I successfully installed Ubuntu along side windows xp and had no issues. I decided to revamp my box and I wiped the drive, installed two fresh copies of xp on two different partitions, and installed Ubuntu on a third. This time, there is no 'other operating systems' option on the grub boot menu. I attempted to amend the grub menu manually and was able to ad a windows option to the grub, but it gave  a 'device not found' error. 

perhaps this has something to do with it 
the windows are installed on /dev/hda5 and /dev/hda6
and Ubuntu is on /dev/da8

I didn't do anything different during the second install of Ubuntu. Any advice?

---

### Post by nixclusive on 2007-09-28
when you start the computer and the grub menu is shown, press 'c' to enter the grub shell. Now enter the following commands,
```

root (hd0,5)
makeactive
chainloader +1

```

Play with the line "root (hd0,5)", you can change the two digits, press TAB anytime while typing and grub will autocomplete for you. note down what works and edit the file /boot/grub/menu.lst in ubuntu afterwords.

And don't let that ruin your life.. it's only a computer. :) [no offence intended]

---

### Post by CptnFantasy on 2007-09-28
I received 'Error Message 12: Specified device is inactive'
do I need to mount the drive or something?
maybe something went wrong with the installation?

---

### Post by lgcabarcas on 2007-09-28
the ones that you put at the beginnig of the post was thge full set of partitions you have? if not plz give the full info just to get the whole picture

---

### Post by Sef on 2007-09-28
Copy and paste what your partitions set up is.

Applications > Accessories > Terminal

then type  this:   sudo fdisk -l

then copy and paste it here.

---

### Post by CptnFantasy on 2007-09-28
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        4864    39070048+   f  W95 Ext'd (LBA)
/dev/hda5            2041        3453    11349891    7  HPFS/NTFS
/dev/hda6            3454        4864    11333826    7  HPFS/NTFS
/dev/hda7               1         492     3951895+  82  Linux swap / Solaris
/dev/hda8             493        2040    12434278+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       38913   312568641    7  HPFS/NTFS

windows is on hda5 and hda6

---

### Post by CptnFantasy on 2007-09-28
I reinstalled windows on hda1 and hda5 now ubuntu recognizes it

---

