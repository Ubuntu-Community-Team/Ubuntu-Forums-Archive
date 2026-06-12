---
title: "Automount issues"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by MosesS on 2007-03-19
Hi all,

having some problems with automounting my windows partitions from the other hard drive.

I have tried going through old posts but no solution works:( Below is fstab and fdsik -l

It's the 163GB Drive that is not mounting at startup

Any help much appreciated

Thnx

_Fstab_
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a9dd8485-015c-4dde-902e-39948fd256b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=bfae33e5-10b9-454f-8bc7-7822f0458285 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0


_fdisk -l_
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19929   119121975    f  W95 Ext'd (LBA)
/dev/sda5            5100       15935    87040138+   7  HPFS/NTFS
/dev/sda6           15936       19929    32081773+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30024   241167748+  83  Linux
/dev/sdb2           30025       30401     3028252+   5  Extended
/dev/sdb5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 6495 MB, 6495068160 bytes
240 heads, 63 sectors/track, 839 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         839     6342808+   b  W95 FAT32

Disk /dev/sdd: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2432    19535008+   c  W95 FAT32 (LBA)

---

### Post by MosesS on 2007-03-19
Come on peeps

someone please?

---

### Post by justleen on 2007-03-19
your fdisk -l outputs your drive in /dev/sda...

cant see anything else wrong, really..

---

### Post by Bias on 2007-03-19
Can't see any attempt to mount this in the fstab file!

The basic guide covers this:-

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html)

---

### Post by justleen on 2007-03-19
> **Bias said:**
> Can't see any attempt to mount this in the fstab file!

The basic guide covers this:-

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html)

Que?


Yes there is.. last line in his fstab!

Cant open the https link here, bleeding police network, to see what is says there, but on top of my head: thats correct

/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by MosesS on 2007-03-19
These are the drives I would like to mount

/dev/sda2 5100 19929 119121975 f W95 Ext'd (LBA)
/dev/sda5 5100 15935 87040138+ 7 HPFS/NTFS
/dev/sda6 15936 19929 32081773+ b W95 FAT32

---

### Post by Bias on 2007-03-19
> **justleen said:**
> Que?


Yes there is.. last line in his fstab!

Cant open the https link here, bleeding police network, to see what is says there, but on top of my head: thats correct

/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0

Then it would need to be

 /dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by MosesS on 2007-03-19
> **Bias said:**
> Then it would need to be

 /dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0

I shall try and change that then:)

can I ask what the correct input in fstab would be for the other 3 partitions?

cheers

---

### Post by justleen on 2007-03-19
> **Bias said:**
> Then it would need to be

 /dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0

as i suggested in my first reply...

---

### Post by justleen on 2007-03-19
@Moses
it would look like this

/dev/sda2 5100 19929 119121975 f W95 Ext'd (LBA)
/dev/sda5 5100 15935 87040138+ 7 HPFS/NTFS
/dev/sda6 15936 19929 32081773+ b W95 FAT32

/dev/sda5 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sda2 /media/windowstoo	vfat	defaults	0 0
/dev/sda6 /media/morewindows	vfat	defaults	0 0


though, one partition is extented (sda2)! no need to mount that..

---

### Post by MosesS on 2007-03-19
Cheers mate,

just need to find a way to edit fstab now:)

can't find the command I used to do it before

---

### Post by justleen on 2007-03-19
open a terminal:
```
 sudo vi /etc/fstab 
```

or use gedit, if your more comfortable with that :)
(press alt-f2 to execute command, and type sudo gedit /etc/fstab )

---

### Post by MosesS on 2007-03-19
OK movies partition is mounted now.....MP3s one which is sda6 isn't though:(

This is my fstab now

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a9dd8485-015c-4dde-902e-39948fd256b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=bfae33e5-10b9-454f-8bc7-7822f0458285 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2 /media/windowstoo vfat defaults 0 0
/dev/sda5 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sda6 /media/morewindows vfat defaults 0 0

---

