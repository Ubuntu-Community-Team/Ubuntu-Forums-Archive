---
title: "Nfs file permissions"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-02-07
Okay i am having problems being able to write my nfs directory. This si my /etc/exports file on the NFS server it self 
"/media/sfn *(rw,sync,no_subtree_check)"
i have it mounted on my laptop but i dont know what the problem is so please help.

---

### Post by hamstersquasher on 2008-02-07
check your permissions on /media/sfn.  if you aren't using the same username on both boxes (more importantly - same UID) then you may need to add the write permission to the /media/sfn file.  do that by using <b>sudo chmod -R o+w /media/sfn</b>.  If this is on a network with multiple users, just take into consideration the security changes this would bring.

---

### Post by fedex1993 on 2008-02-08
wel i am using the same username but i may need to fix it and what not thanks hamstersquasher love your user name lol

---

### Post by jan quark on 2008-02-08
please run the following terminal commands and post the output thank you

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
ls -l / media
```

---

### Post by fedex1993 on 2008-02-08
fdisk
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19080   153260068+  83  Linux
/dev/hda2           19081       19457     3028252+   5  Extended
/dev/hda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux

```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/nfs      ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
ls -l / media
```
total 12
lrwxrwxrwx 1 root root    6 2008-02-08 15:45 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-02-08 15:45 cdrom0
lrwxrwxrwx 1 root root    7 2008-02-08 15:45 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2008-02-08 15:45 floppy0
drwxr-xrwx 3 root root 4096 2008-02-08 15:44 nfs

```

---

