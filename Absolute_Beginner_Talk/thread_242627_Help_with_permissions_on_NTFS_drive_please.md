---
title: "Help with permissions on NTFS drive please"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Stew2 on 2006-08-23
Hello all,

I cant quite seem to get the permission thing straightened out on my NTFS drive. I would like to be able to look at and copy files (music, pics) from my NTFS drive to my ubuntu installation on another drive. If I go to System> Administration> Disks, I can see the NTFS drive and partition but it will not let me browse it because I dont have permission. If I open nautilus as root, I can look at the files, play music etc. but cannot copy or drag them to my ubuntu desktop. I tried how to's from a few similiar threads but I cant quite get them to work. I am sure I am missing something simple so if someone could help me out I would greatly appreciate it :D . Posted below are the outputs of my fdisk -l and etc/fstab files. Thank you in advance.

Regards,
Stew2

Output of fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2377    19093221   83  Linux
/dev/hdb2            2378        2482      843412+   5  Extended
/dev/hdb5            2378        2482      843381   82  Linux swap / Solaris

Output of fstab below

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by aysiu on 2006-08-23
```
sudo umount /dev/hda1
sudo mkdir /media/windows
sudo nano -B /etc/fstab
``` Add this line ```
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
``` Save (Control-X, Y, Enter). ```
sudo mount -a
```

---

### Post by catlett on 2006-08-23
removed.... already taken care of

---

### Post by Stew2 on 2006-08-23
> **aysiu said:**
> ```
sudo umount /dev/hda1
sudo mkdir /media/windows
sudo nano -B /etc/fstab
``` Add this line ```
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
``` Save (Control-X, Y, Enter). ```
sudo mount -a
```

:D Thank you, thank you, thank you!! :D 

That did the trick! Exactly what I was looking for. I had tried almost the exact same thing from a similiar thread that you had answered a while back, but I think I screwed something up when I was editing the fstab file. Thank you very much Aysiu for the quick help, and thank you Catlett for responding as well. It's people like you two that make this OS so great :D .

Regards,
Stew2

---

