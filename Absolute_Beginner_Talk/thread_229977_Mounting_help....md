---
title: "Mounting help..."
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-08-05
Hi

I have several devices that require mounting including one internal hard drive, a CD player and an external hard drive.  Below is a screenshot of the message I get if I try to open from them 'Places' > 'Computer'.  

Can anyone please explain how I go about mounting them?


Thank you for your help.


Regards

---

### Post by moma on 2006-08-05
Can you dive into the command line and report output of the following commands. 
Start command line Terminal from Applications -> Accessories menu.

Note it's lower case L, not a number.
$ [COLOR="Green"]sudo fdisk -l [/COLOR]

$ [COLOR="Green"]cat /etc/fstab [/COLOR]

---

### Post by Norfolk 'n' Good on 2006-08-05
This is the content of sudo fdisk -l

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/hda2            7140        9619    19920600   83  Linux
/dev/hda3            9620        9729      883575    f  W95 Ext'd (LBA)
/dev/hda5            9620        9729      883543+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7179    57665286    7  HPFS/NTFS
/dev/hdb2            7180        9621    19615365   83  Linux
/dev/hdb3            9622        9729      867510    f  W95 Ext'd (LBA)
/dev/hdb5            9622        9729      867478+  82  Linux swap / Solaris

and this the content of cat /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I hope this information is useful.

---

### Post by moma on 2006-08-05
Edit /etc/fstab.  Use eg. kate, nano or gedit editor. 
$ [COLOR="Green"]sudo gedit /etc/fstab [/COLOR]

Add this line for /dev/hdb2  (the filesystem type is most likely ext3)
```
/dev/hdb2  /media/hdb2 ext3  defaults  0 2
```
You can add these lines for Windows NTFS partitions (/dev/hda1 and hdb1). It will give you  read-only access.
```
/dev/hda1   /media/hda1  ntfs  nls=utf8,umask=0222 0    0
/dev/hdb1   /media/hdb1  ntfs  nls=utf8,umask=0222 0    0
```
--------------------------------------------
You must also create the mount(point) directories
$ [COLOR="Green"]sudo  mkdir /media/{hdb2,hda1,hdb1}[/COLOR]

Restart nautilus or run this command (it will remount the entries in /etc/fstab)
$ [COLOR="Green"]sudo mount -a[/COLOR]
or
$ [COLOR="Green"]sudo mount -a -o remount[/COLOR]
---------------------------------------------
Guides:
[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")

[http://psychocats.net/ubuntu/mountwindows.php]("http://psychocats.net/ubuntu/mountwindows.php")

---

### Post by FarmerGiles on 2006-08-05
Thanks moma :D 

you helped me sort out my first problem without even knowing!

I couldn't see my NTFS partition so looked here for help, I found it;) 

Great work!

---

