---
title: "Need to back up my files to another partition....."
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by boyturtle on 2007-10-17
....but dont seem to have permision to write on the ext3 partition that I created. Will it work if I changed the partition to fat32 or ntfs? Is there a simple work around please? :confused:

---

### Post by yabbadabbadont on 2007-10-17
Where did you tell it to mount the new ext3 partition that you created?

---

### Post by boyturtle on 2007-10-18
Erm, I didnt.  What do I need to do here please?

---

### Post by Inxsible on 2007-10-18
Open a terminal and type in these commands.
Post the output here

```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by boyturtle on 2007-10-18
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       22490   180650893+  83  Linux
/dev/sda2           29133       29509     3028252+  82  Linux swap / Solaris
/dev/sda3   *       29510       30401     7164990   83  Linux
/dev/sda4           22491       29132    53351865   83  Linux

Partition table entries are not in disk order

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

and 

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e87375bd-99d2-4be8-a3f4-f38017f21ad3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=8faf2399-7f69-4eaf-b8f6-a7e0c628e20a none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

I would like to be able to write to the windows disk and the dev/sda4 partition. Currently I can read the windows partition but not the linux one (I altered the mount point to \ in propereties>volume>settings and it wont go back to its default now I have altered that!!), all that I see is the \ directory.
I currnetly have 2 hard drives as I wasnt able to get the unit to dual boot. I am going to try again with gutsy but I need to save quite a lot of stuff to the other hard drive first
Cheers

---

