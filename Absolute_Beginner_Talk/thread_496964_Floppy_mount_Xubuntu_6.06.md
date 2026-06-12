---
title: "Floppy mount Xubuntu 6.06"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by oiler on 2007-07-09
Cannot get floppy to mount on Via C3 desktop Microtel. CD and USB work fine.  Need floppy for quick copies.  Below is contents of Fstab and error message returned in terminal mode.  New user.
fstab contents:
moun# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
terminal message:
cafe@cafe-desktop:~$ sudo mount media/floppy0
Password:
mount: can't find media/floppy0 in /etc/fstab or /etc/mtab
cafe@cafe-desktop:~$ sudo mount dev/fd0
mount: can't find dev/fd0 in /etc/fstab or /etc/mtab
cafe@cafe-desktop:~$ sudo mount -a
cafe@cafe-desktop:~$

contents of media file:
file:///media/floppy0
file:///media/cdrom0
file:///media/cdrom

Any help would be greatly appreciated.

---

### Post by confused57 on 2007-07-10
You left out the root (/) in your path:
```
sudo mount /media/floppy0
sudo mount /dev/fd0
```

---

### Post by oiler on 2007-07-10
Thanks-a little careless there.  Your correction produced the following:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0


sudo mount /media/floppy0
mount: you must specify the filesystem type
cafe@cafe-desktop:~$ mount /dev/fd0
mount: I could not determine the filesystem type, and none was specified
cafe@cafe-desktop:~$

Floppy drive was recognised but that was as far as it went.

oiler

---

### Post by confused57 on 2007-07-10
You might try:
```
sudo mount /dev/fd0 /media/floppy0
```

---

### Post by insomniacpyro on 2007-07-10
Just a question: Do you have a disk in the drive when you try to mount it? Mine won't unless I put one in.

---

### Post by oiler on 2007-07-12
Yep- disk was in drive and checked on another computer to be sure disk was readable.

oiler

---

