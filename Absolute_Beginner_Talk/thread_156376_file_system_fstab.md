---
title: "file system fstab"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by SVwanders on 2006-04-06
I really screwed up my file system trying to get access to my second hard drive. Before I edited /etc/fstab I made a backup . . . so far so good. But by a couple days later I had forgotten what I had done and only after I made another backup . . . backing up the incorrect information did I realize I am screwed. 

As I said I have two hard drives:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32        4865    38829105    5  Extended
/dev/hdb5              32        4865    38829073+  8e  Linux LVM

Now I need to know how to edit fstab to get my file system working again. The edited file is below. Can anyone help this absolute beginner get this file correctly edited:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /boot           ext3    defaults        0       2
/dev/hdb5       /media/hdb5     vfat    iocharset=utf8,umask=000
/dev/hdb2  /media/windows       ntfs    udf,defaults,umask=0222  0  0
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thank you, tim

---

### Post by amohanty on 2006-04-06
As fas as I can tell it all looks good. What kind of trouble are you running into?

AM

---

### Post by SVwanders on 2006-04-06
I am not sure that the information in the fstab is correct. As it is booting it fails the file system check. So some info concerning hard drive one and two might be incorrect. I pretty much had to guess at what it should be. Also I can't access my other hard drive no matter what I do. It's there! As the first system message tell me . . . maybe it is an IO error . . . idiot operator!

---

### Post by Sutekh on 2006-04-06
[QUOTE=SVwanders]
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1[/quote]I don't know what /dev/mapper/Ubuntu-root means.
[QUOTE=SVwanders]
/dev/hdb1       /boot           ext3    defaults        0       2
[/quote]I would have thought that the bootable partition /dev/hdb1 would be / in the fstab not /boot.  I could be wrong though  Does this have something to with the /dev/mapper/Ubuntu-root thing?
[QUOTE=SVwanders]
/dev/hdb5       /media/hdb5     vfat    iocharset=utf8,umask=000
[/quote]Why does fdisk output this partition as **Linux LVM**.  I don't knw anything about LVM, but I assume that if it is a Linux partition then **vfat** in the fstab isn't good

[QUOTE=SVwanders]
/dev/hdb2  /media/windows       ntfs    udf,defaults,umask=0222  0  0
[/QUOTE]
This is a problem, because /dev/hdb2 is an extended partition, which encompases /dev/hdb5, its not a partition in itself.


This is a long shot but there may be a /etc/fstab~ file, which is an automatic backup file.  What's that look like?

---

### Post by amohanty on 2006-04-06
> I don't know what /dev/mapper/Ubuntu-root means.

Thats the LVM volume name, which is kind of strange that your root drive is on the LVM, and why are you using LVM anyways?

I suggest that you plug in a spare hdd, or wipe out one of them (if you can afford to lose data, buy a spare used one - always useful, dirt cheap - look on simething akin to craigslist). Use a Live cd to boot up and then do an [fsck]("http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=fsck+manual")

> maybe it is an IO error . . . idiot operator!
I thin kwhat you are looking for is [PEBKAC]("http://ars.userfriendly.org/cartoons/?id=19980506&mode=classic") :)

HTH
AM

---

