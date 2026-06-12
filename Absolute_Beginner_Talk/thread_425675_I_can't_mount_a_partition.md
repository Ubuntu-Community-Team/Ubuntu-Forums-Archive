---
title: "I can't mount a partition"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by kai_haider on 2007-04-27
I can't mount the partition for /dev/sdb2 although I can mount /dev/sdb1
I've tried reformatting the partition and a few other things that have made no differance.
when I try to mount it I get this error:
$ mount -a
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/fde71312-7242-4e73-bbdb-8adb8db51561,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

when I look at the uuid I see this:
$ ls /dev/disk/by-uuid -lh
total 0
lrwxrwxrwx 1 root root 10 2007-04-27 16:17 01d73068-4664-4d58-9b12-b7d00b5cecba -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-04-27 16:17 13473570-a698-4cbb-a477-e10afd0ab69d -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-04-27 16:17 CC04-58F9 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-04-27 16:17 fde71312-7242-4e73-bbdb-8adb8db51561 -> ../../sdb2


And this is the fstab I have:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=01d73068-4664-4d58-9b12-b7d00b5cecba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=fde71312-7242-4e73-bbdb-8adb8db51561 /media/auraya   ext3    defaults,unmask=000        0       2
# /dev/sdb1
UUID=CC04-58F9  /media/winxp    vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda5
UUID=13473570-a698-4cbb-a477-e10afd0ab69d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

If you have any advice I would be very grateful, thanks.

---

### Post by Najand on 2007-04-27
> **kai_haider said:**
> I can't mount the partition for /dev/sdb2 although I can mount /dev/sdb1
I've tried reformatting the partition and a few other things that have made no differance.
when I try to mount it I get this error:
$ mount -a
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/fde71312-7242-4e73-bbdb-8adb8db51561,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

when I look at the uuid I see this:
$ ls /dev/disk/by-uuid -lh
total 0
lrwxrwxrwx 1 root root 10 2007-04-27 16:17 01d73068-4664-4d58-9b12-b7d00b5cecba -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-04-27 16:17 13473570-a698-4cbb-a477-e10afd0ab69d -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-04-27 16:17 CC04-58F9 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-04-27 16:17 fde71312-7242-4e73-bbdb-8adb8db51561 -> ../../sdb2


And this is the fstab I have:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=01d73068-4664-4d58-9b12-b7d00b5cecba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=fde71312-7242-4e73-bbdb-8adb8db51561 /media/auraya   ext3    defaults,unmask=000        0       2
# /dev/sdb1
UUID=CC04-58F9  /media/winxp    vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda5
UUID=13473570-a698-4cbb-a477-e10afd0ab69d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

If you have any advice I would be very grateful, thanks.

First change your fstab to:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=01d73068-4664-4d58-9b12-b7d00b5cecba /               ext3    defaults,errors=remount-ro 0       1
#UUID=fde71312-7242-4e73-bbdb-8adb8db51561
/dev/sdb2       /media/auraya   ext3    defaults,unmask=000        0       2
# /dev/sdb1
UUID=CC04-58F9  /media/winxp    vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda5
UUID=13473570-a698-4cbb-a477-e10afd0ab69d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
 And try again.

If it doesn't work. Try fsck the partition and see if there are some bad superblocks and fix them.

---

### Post by kai_haider on 2007-04-27
When I tried that fstab I got:
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and I'm not sure how to use fsck...I tried:
$ fsck /dev/sdb2
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sdb2: clean, 11/8552448 files, 314441/17097176 blocks

---

### Post by Najand on 2007-04-27
Try to force checking even if filesystem is marked clean; i.e. "fsck -f" command!

---

### Post by kai_haider on 2007-04-27
you mean this?

$ fsck -f /dev/sdb2
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb2: 11/8552448 files (9.1% non-contiguous), 314441/17097176 blocks

---

### Post by Najand on 2007-04-27
Hmm... Can you copy/paste the output of:
```

sudo fdisk -l

``` here?

---

### Post by kai_haider on 2007-04-27
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9359    75176136   83  Linux
/dev/sda2            9360        9733     3004155    5  Extended
/dev/sda5            9360        9733     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6079    48829536    b  W95 FAT32
/dev/sdb2            6080       14593    68388705   83  Linux

---

### Post by Najand on 2007-04-27
OK, what if you try mounting it manually:
```

sudo mount -t ext3 /dev/hdb2 /media/auraya

```

---

### Post by kai_haider on 2007-04-27
OMG, that worked!

chmod even worked to give me full acces, thanks :D

Do you have an idea on how to fix the fstab though?

---

### Post by Najand on 2007-04-27
Well, probably you must rewrite options in your fstab file.
Change it to:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=01d73068-4664-4d58-9b12-b7d00b5cecba /               ext3    defaults,errors=remount-ro 0       1
#UUID=fde71312-7242-4e73-bbdb-8adb8db51561
/dev/sdb2       /media/auraya   ext3    defaults,rw,users,umask=000        0       2
# /dev/sdb1
UUID=CC04-58F9  /media/winxp    vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda5
UUID=13473570-a698-4cbb-a477-e10afd0ab69d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by kai_haider on 2007-04-27
I tried updating fstab and then doing:

$ umount /media/auraya
$ mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

=/

damn

---

### Post by Najand on 2007-04-27
Can you copy and paste your new fstab file here again? I want to check something.

---

### Post by kai_haider on 2007-04-27
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=01d73068-4664-4d58-9b12-b7d00b5cecba /               ext3    defaults,errors=remount-ro 0       1
#UUID=fde71312-7242-4e73-bbdb-8adb8db51561
/dev/sdb2       /media/auraya   ext3    defaults,rw,users,umask=000        0       2
# /dev/sdb1
UUID=CC04-58F9  /media/winxp    vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda5
UUID=13473570-a698-4cbb-a477-e10afd0ab69d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Najand on 2007-04-27
change that "2" at the end of the 8thj line to zero, save it and try to mount it again.

---

### Post by kai_haider on 2007-04-27
I think that was it. Thanks so much :D

Do you know what that line does?

---

### Post by Najand on 2007-04-27
It is for "fsck"ing the filesystem during bootup... I don't know why you have such problem though... If that field is not present or zero, a value  of  zero is  returned  and fsck will assume that the filesystem does not need to be checked.

---

### Post by kai_haider on 2007-04-27
that's strange, but it's working yea ^_^

---

### Post by Najand on 2007-04-27
Good to know that.

---

### Post by kai_haider on 2007-04-27
Really, thank you so so much :)

---

