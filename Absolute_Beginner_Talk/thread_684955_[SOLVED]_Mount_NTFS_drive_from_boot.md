---
title: "[SOLVED] Mount NTFS drive from boot"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by H3retic on 2008-02-01
I want to mount two ntfs drives from boot, and have them appear on the desktop.  I don't want to have to put in a password to acess them either.  All the tutorials to do this seem to be outdated.

Help!

---

### Post by taurus on 2008-02-01
You need to add two entries on /etc/fstab to have them mounted at boot.  What are the partitions of those two ntfs drives anyway?  Post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by H3retic on 2008-02-01
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10ab10aa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3433    27575541    7  HPFS/NTFS
/dev/hda2            3434        4798    10964362+  83  Linux
/dev/hda3            4799        4865      538177+   5  Extended
/dev/hda5            4799        4865      538146   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x052761f2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        2551    20482875    f  W95 Ext'd (LBA)
/dev/hdb2            2552       24321   174867525    7  HPFS/NTFS





sean@sean-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=90a9be3f-0264-4afc-97cc-7c2c5687f231 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=99f956a5-4437-476d-ae2d-df4ee1c0be54 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
sean@sean-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              11G  2.6G  7.5G  26% /
varrun                506M  208K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
tmpfs                 506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile

---

### Post by taurus on 2008-02-01
So, looks like you want to mount /dev/hda1 & /dev/hdb2.  Edit /etc/fstab from a terminal with

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hda1   /media/hda1   ntfs-3g   defaults   0   0
/dev/hdb2   /media/hdb2   ntfs-3g   defaults   0   0
```
Save it and close down gedit editing window.  Then, install ntfs-3g driver, create those two new mount points, and mount them.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hda1 /media/hdb2
sudo mount -a
df -h
```
Two two ntfs partitions will be mounted to /media/hda1 & /media/hdb2 from now on, every time you boot Ubuntu.

---

### Post by H3retic on 2008-02-01
You are a linux god among men.  Thank you, it worked like a charm.

---

### Post by Frinky on 2008-07-09
I had the same problem but had tried to change /etc/fstab myself without reading this thread and had no success. I eventually reverted /etc/fstab to what it had been and followed the instructions here.

Worked like a dream. THANK YOU!

---

### Post by FlyingIsFun1217 on 2008-07-09
Another user helped by this. hda1 wasn't being mounted upon bootup, as it used to (for some reason).

FlyingIsFun1217

---

