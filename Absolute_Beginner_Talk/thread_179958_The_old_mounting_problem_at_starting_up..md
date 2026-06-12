---
title: "The old mounting problem at starting up."
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Dutch on 2006-05-21
Yep , the old starting up problem.
I get a message: failed mounting local file system.

Dit some looking around on the net and the forum, this is what I can tell:

```

paulaccount@PaulIBM:~$ fdisk -l
paulaccount@PaulIBM:~$ sudo fdisk -l
Password:

Schijf /dev/hda: 80.0 GB, 80032038912 bytes
255 koppen, 63 sectoren/spoor, 9730 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/hda2            9412        9730     2562367+  1c  Verborgen W95 FAT32 (LBA)
/dev/hda3            1825        3648    14651280   83  Linux
/dev/hda4            3649        9411    46291297+   5  Uitgebreid
/dev/hda5            3649        9241    44925741   83  Linux
/dev/hda6            9242        9411     1365493+  82  Linux swap / Solaris

Partitietabel ingangen zijn niet in schijfvolgorde
paulaccount@PaulIBM:~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda2       /media/hda2     vfat    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/hda1/windows ntfs nls=utf8,umask=0222 0 0
/media/ipod  /mnt/ipod vfat user,noauto,umask=000 0 0
paulaccount@PaulIBM:~$

```

Are u the person that has the solution ?

---

### Post by KarmaKing on 2006-05-21
I just went through this whole thing  and found these link especially helpful.
[http://www.ubuntuforums.org/showthread.php?t=174562](http://www.ubuntuforums.org/showthread.php?t=174562)

I followed this one to the letter and got it to work
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

good luck

KK

---

### Post by chettyk on 2006-05-21
Your fstab is mountng the same partition twice. Remove one of the two lines. Or else put a hash mark (#) at the beginning of the fstab line that you want to make inactive.

[code]
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda1 /media/hda1/windows ntfs nls=utf8,umask=0222 0 0
[/code

---

