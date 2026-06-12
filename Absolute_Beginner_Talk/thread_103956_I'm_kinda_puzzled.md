---
title: "I'm kinda puzzled"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by cvcaelen on 2005-12-15
when I type sudo fdisk-l  I get :
```
Schijf /dev/sda: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/sda1   *           1        5904    47423848+   7  HPFS/NTFS
/dev/sda2            5905        7896    16000740    f  W95 Ext'd (LBA)
/dev/sda3            7897        9729    14723572+  83  Linux
/dev/sda5            5905        7813    15334011    b  W95 FAT32
/dev/sda6            7814        7896      666666   82  Linux swap / Solaris

```

where I am expecting: hda1 or something for the hard disks ???

thanks for clearing things up
Christiaan

edit : found it :sda = scsi ; fda = ide

---

### Post by GreyFox503 on 2005-12-15
hda usually is for IDE hard drives (parallel ATA)

It looks like you have a newer SATA drive (the abreviation is sda).

---

### Post by cvcaelen on 2005-12-15
thanks , greyfox

on to the next level :)

when I type : fstab
I get :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

sda 1 , 2 and 5 don't show
I'm trying to mount them

Thanks in advance

Christiaan

---

### Post by Lambert on 2005-12-15
If you just want to mount the drive when ever you would use the mount command. to understand it go [here]("http://www.tuxfiles.org/linuxhelp/mounting.html").  For more information on mount you can also look at the man page. *man mount *man pages are a little hard to read at first but take the time to understand them. They're a good resource.

If you want to mount the driver everytime it boots you need to edit your /etc/fstab file and ad a line to mount what you want. For more on editing fstab go [here]("http://www.tuxfiles.org/linuxhelp/fstab.html").

---

### Post by cvcaelen on 2005-12-15
Thanks very much :) 
just what I needed

Christiaan

---

### Post by GreyFox503 on 2005-12-16
To clarify a bit:

That /etc/fstab file doesn't show or "detect" anything connected to your computer, it is just a text file that shows you what devices are automatically mounted at startup (although you can put things like removable devices in there to make your life easier).

Use the mount command for temporary things like CDs or floppies.  To permanently mount something, add it to your /etc/fstab file, like Lambert described.

---

