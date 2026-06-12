---
title: "Please help, urgent: windows started to format my HD"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2006-10-30
Hi,

Today i wanted to install XP (for gaming),
so i made a partition of 20Gb on my hdc (don't have hda/hdb, only hdc and hdd)

So my hdd looked like this:
40Gb Dapper home
10Gb Dapper root
20Gb Fat32
and some other partitions

I rebooted, with the XP cd in the drive,
and waited,
a long time..

After that waiting, i could choose where to install XP:
chose the 20Gb Fat32 partition. Windows asked me if it could format that partition, so i said 'yes'.

Then the progress bar stated: 131000Mb being formated :?

Before it even moved my hard drive, i pressed reboot.

Now the problem is:
My hdd isn't recognised as 3 partitions, but as 1 partition of 128Gb.

How can i tell Ubuntu that the hdd is actually consistant of more partitions?

I believe one was ext3, ext2, and a NTFS was also there (not _that_ important, but hey)

Here's the output of ```
sudo fdisk -l
```
```
Schijf /dev/hdc: 251.0 GB, 251000193024 bytes
86 koppen, 15 sectoren/spoor, 380026 cylinders
Eenheden = cylinders van 1290 * 512 = 660480 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdc1   *           1      208090   134217727+   4  FAT16 <32M

Schijf /dev/hdc1: 137.4 GB, 137438952960 bytes
86 koppen, 15 sectoren/spoor, 208089 cylinders
Eenheden = cylinders van 1290 * 512 = 660480 bytes

   Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdc1p1   *           1      208090   134217727+   4  FAT16 <32M

Schijf /dev/hdd: 122.9 GB, 122942324736 bytes
255 koppen, 63 sectoren/spoor, 14946 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdd1               1         522     4192933+  83  Linux
/dev/hdd2             523        1827    10482412+  83  Linux
/dev/hdd3            1828        4438    20972857+   b  W95 FAT32

```


Iarwain

---

### Post by podunk on 2006-10-30
Ouch! That looks bad. :-(  You might give this a try:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
The manual is in both English and German

The only time I had to recover a hard drive I used this and it worked good:
[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

---

### Post by Iarwain ben-adar on 2006-10-30
Hi podunk,
I LOVE YOU MAN!! :D

Now,
testdisk sees the partitions, but i'm unsure how to get them back..


Iarwain

---

### Post by Iarwain ben-adar on 2006-10-30
Update:
nevermind,
i just Entered, and followed the things they said :D

Sometimes i'm still quite the noob :D


Iarwain

---

