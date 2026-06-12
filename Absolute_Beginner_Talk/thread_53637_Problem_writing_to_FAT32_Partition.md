---
title: "Problem writing to FAT32 Partition"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by Josh4518 on 2005-08-01
I set up a 30GB Hard Drive in 3 Partitions, one 10GB for Windows. one 10GB for Ubuntu and one 10GB to share files between the two OS. Windows is NTFS, Ubuntu is ext3 and the shared partition is FAT32.

I mounted the Windows and Shared drive following the UbuntuGuide, both mounted succesfully. However I cannot write to the FAT drive. When I try to change the permissions I get "You are not the owner, so you can't change these permissions" The owner is listed as root. Any help would be much appreciated. Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /media/shared   vfat    iocharset=utf8,umask=000   0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by frodon on 2005-08-01
try that :```
 # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda5 /media/shared vfat **rw,user,**iocharset=utf8,umask=000 0 0
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```It will allow you to write on your FAT partition as a simple user

---

### Post by Josh4518 on 2005-08-01
Tried it, but didn't work. Thanks though.

---

### Post by frodon on 2005-08-01
have you rebooted your computer ?
this is my fstab file, maybe it could help you : ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1	/mnt/disk	vfat	rw,user,exec,umask=0		0	0
/dev/hdd5	/mnt/disk_video	vfat	rw,user,exec,umask=0		0	0
```

---

### Post by Josh4518 on 2005-08-01
Yeah I rebooted after I edited the fstab, I'll take a look at yours when I'm on my Ubuntu computer.

---

### Post by Omnios on 2005-08-01
I while ago I tryed mounting a vfat drive as my username to set up wine on it which did not work but I successfully mounted as user, I added a link to the thread also explains a lot about mounting. 

[http://ubuntuforums.org/showthread.php?t=49830](http://ubuntuforums.org/showthread.php?t=49830) 

 Another aspect of mounting a vfat in Linux is carry over stuff from windows, I found some files had permition problems this can be changed by changing the permitions in terminal. Also listed on the forems is a open as root script for graphical file management that may make you life easier in that aspect. Ill see if I can find the link.

---

### Post by Josh4518 on 2005-08-01
Thanks Omnios, that thread you linked to got it working :)

---

