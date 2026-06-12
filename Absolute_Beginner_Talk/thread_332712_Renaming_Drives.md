---
title: "Renaming Drives"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-01-06
I have some windows drives that I would like to give more meaningful name to.

I tried editing the fstab to add a LABEL entry to each line.  Drive did not show up after rebooting.

I tried using the tune2fs command but it came back and said some magic number was bad.

I tried to use the Disk Manager and make it point to /media/NewName but that did not work either.

I selected the HardDrive icon on the desktop and selected properties, but the name was not editable.

So how do you change it?

---

### Post by taurus on 2007-01-06
When you change the mount point in /etc/fstab, /media/NewName, you need to create that new mount point or it won't be mount (can't since there is no new mount point for it to mount)...

Applications -> Accessories -> Terminal
```
sudo mkdir /media/NewName
```

Then you have to reboot.

---

### Post by weaver4 on 2007-01-06
OK thanks, that fixed all but one of them.

my /dev/sba1 is still called "New Volume",  Any ideas, here is my fstab file.

===========================================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/winC     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/winD     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /media/winShared     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/winE     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-01-06
The entry for /dev/sda6 should look like this!

```

/dev/sda6  /media/winShared  vfat  defaults,**iocharset=**utf8,umask=007,gid=46  0  1

```
What's the output of this command from a terminal?

```
ls -la /media
```
Have you tried to reboot your machine?

---

### Post by weaver4 on 2007-01-06
Here is the results.

And yes; I did try to reboot.

=================================

trey@trey-desktop:~$ ls -la /media
total 73
drwxr-xr-x 12 root root     4096 2007-01-06 19:23 .
drwxr-xr-x 21 root root     4096 2007-01-04 18:21 ..
lrwxrwxrwx  1 root root        6 2007-01-03 22:35 cdrom -> cdrom0
dr-xr-xr-x  1 root root      128 2006-10-31 21:48 cdrom0
drwxr-xr-x  2 root root     4096 2007-01-03 22:35 hda1
drwxr-xr-x  2 root root     4096 2007-01-03 22:35 sda1
drwxr-xr-x  2 root root     4096 2007-01-03 22:35 sda6
drwxr-xr-x  2 root root     4096 2007-01-03 22:35 sdb1
dr-xr-x---  1 root plugdev 32768 2007-01-06 12:32 winC
drwxr-xr-x  2 root root     4096 2007-01-05 18:18 win-C
dr-xr-x---  1 root plugdev  4096 2007-01-04 04:22 winD
dr-xr-x---  1 root plugdev  4096 2007-01-03 17:14 winE
drwxrwx---  3 root plugdev  4096 1969-12-31 19:00 winShared
trey@trey-desktop:~$

---

### Post by taurus on 2007-01-06
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by weaver4 on 2007-01-06
Here you go.

=======================================

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19760   158722168+   7  HPFS/NTFS
/dev/sda2           19761       24321    36636232+   5  Extended
/dev/sda5           24067       24321     2048287+  82  Linux swap / Solaris
/dev/sda6           23404       24066     5325516    b  W95 FAT32
/dev/sda7           19761       23403    29262334+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   42  SFS

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10010    80405293+   7  HPFS/NTFS
trey@trey-desktop:~$

---

### Post by taurus on 2007-01-06
So every drive has a right name, mount point, on your Desktop except /dev/sda1!!!

---

### Post by weaver4 on 2007-01-06
> **taurus said:**
> So every drive has a right name, mount point, on your Desktop except /dev/sda1!!!

Yep, Everyone is right but that one.

---

### Post by taurus on 2007-01-06
I am not sure why and you can't change the name from the Properties either (right click on the icon).

---

### Post by weaver4 on 2007-01-07
Well I did a complete search on my ubuntu install for "New Volume" and could not find anything to change.  So I figured it must be on the HD itself.  Booted into windows, right clicked on the drive and sure enough it was called "New Volume".  So I changed the name of the drive from "New Volume" to "" (nothing).  Rebooted and it was then called "winD" just like I had in my fstab file.

Probably could not right click and change it because it was a NTFS extension and ubuntu could not write to it.

Hope this helps someone else.

---

