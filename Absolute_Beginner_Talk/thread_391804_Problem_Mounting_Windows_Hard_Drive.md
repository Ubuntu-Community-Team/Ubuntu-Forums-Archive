---
title: "Problem Mounting Windows Hard Drive"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by IgnacioMiller on 2007-03-23
I put a Windows hard drive in my computer to pull some files off of it for my friend. While I was at it I decided to mount my own Windows partition. Here is fdisk -l:

```
dan@dan-desktop-linux:~$ sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5293    42515991    7  HPFS/NTFS
/dev/hda2            5294       14215    71665965   83  Linux
/dev/hda3           14216       14593     3036285    5  Extended
/dev/hda5           14216       14593     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+   7  HPFS/NTFS

```

Here is my fstab file (after I edited it for the two new partitions):
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8ac63de2-7984-40f9-b0d7-f89acb07e382 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6ccc32ca-be92-4f3d-b748-9aa1b8eef155 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /jake vfat iocharset=utf8,umask=000 0 0

```

I followed the directions detailed here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Unfortunately, when I follow the last step, mount-a I get this error message:
```
mount: /dev/hda1 already mounted or /windows busy
mount: according to mtab, /dev/hda1 is mounted on /mnt/ntfs1
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
*And after a restart I get this:
```
 wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Any ideas on what I did wrong and how I can fix it?

Thanks,
Ignacio

---

### Post by martinw89 on 2007-03-23
Well it looks like from fsidk -l that his disc is NTFS, but you have your fstab setup as if hdb1 was FAT (vfat).  Try changing```
/dev/hdb1 /jake vfat iocharset=utf8,umask=000 0 0
``` to ```
/dev/hdb1 /jake ntfs nls=utf8,umask=0222 0 0
```

---

### Post by taurus on 2007-03-23
/dev/hdb1 is ntfs not vfat so you need to modify your /etc/fstab to change the filesystem from vfat to ntfs.

```

/dev/hdb1   /jake   ntfs     nls=utf8,umask=0222   0   0

```
Then reboot.

---

### Post by IgnacioMiller on 2007-03-23
D'oh, thanks guys, that did the trick. It's amazing how quickly you can get replies here, this is great! =D

---

### Post by martinw89 on 2007-03-23
No problem, glad you're enjoying Ubuntu also :)

---

