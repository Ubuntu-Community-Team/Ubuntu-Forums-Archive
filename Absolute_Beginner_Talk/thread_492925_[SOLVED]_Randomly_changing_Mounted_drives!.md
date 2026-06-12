---
title: "[SOLVED] Randomly changing Mounted drives??!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-07-05
Hi i've been getting this really inconsistent problem with mounting drives - i had this problem with only read access enabled for my NTFS drives - I've since edited my fstab so i can have read and write access to my NTFS partitions - i thought the problem went away but it dosen't look like it. 

It dosen't make any sense, the mounts will work perfectly one time then be all jumbled the next time... 

and when i check the mounts on my desktop when they are mounted they're not mounting in the right folders - it's like they change their "/dev/***" locations. eg: on this log in i'm on at the moment i'll click on the Windows Disk icon on my desktop and it takes me to "/media/everythingmusic" but with windows mounted within there. My windows partition is supposed to be in /dev/sdc1 and go to /media/windows
instead it looks like it's changed to /dev/sda1 and is now therefore mounting in /media/everythingmusic/

- how can HDDs just change like that in different logins without me making any changes to anything?

anyway i've included the info below incase it's useful


this is my fdisk -l with the drives jumbled up (in this log in i'm in at the moment): - i'll post one with the working fdisk-l when it works at random in the next couple of logins
```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       36480   231585007+   f  W95 Ext'd (LBA)
/dev/sda5            7650       36480   231584976    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   42  SFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      620181   312571192+  42  SFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9352    75119908+  83  Linux
/dev/hdc2            9353        9729     3028252+   5  Extended
/dev/hdc5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19457   156288321   42  SFS

```

ok i've just logged in again and randomally enough it's working again - here's the fdisk -l this time:

```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666   42  SFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      620181   312571192+  42  SFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9352    75119908+  83  Linux
/dev/hdc2            9353        9729     3028252+   5  Extended
/dev/hdc5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19457   156288321   42  SFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650       36480   231585007+   f  W95 Ext'd (LBA)
/dev/sdc5            7650       36480   231584976    7  HPFS/NTFS

```




my fstab looks like this: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=d5b43a11-d3d3-4ff9-bbf8-17bc2c6f811b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=045e2f5e-3b5a-45ab-af4b-f0d3480a460b none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0

## Read and write access to NTFS partitions
# drive /dev/sda
/dev/sda1   /media/everythingmusic   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sda2   /media/movies   ntfs-3g  defaults,locale=en_US.utf8    0    0
# drive /dev/sdb
/dev/sdb1   /media/seriessamplesmartial   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb2   /media/utorrent   ntfs-3g  defaults,locale=en_US.utf8    0    0
# drive /dev/sdc
/dev/sdc5   /media/animations   ntfs-3g  defaults,locale=en_US.utf8    0    0
# drive /dev/hdd
/dev/hdd1   /media/broken   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of read and write access to NTFS partitions

# WindowsXP NTFS read only partiton: (sdc1)
/dev/sdc1   /media/windows   ntfs nls=utf8,umask=0222 0 0
```

---

### Post by ggaaron on 2007-07-05
Let's assume you have one sata hard drive - it's /dev/sda, now you plug in usbdrive1 - it's /dev/sdb, plug in usbdrive2 - it's sdc, now plug out all usbdrives, plug in usbdrive2 - i't /dev/sdb - it has changed from the last plug in, moreover /dev is known to change drive's names without reason.

What you need to do is:
```
ls -la /dev/disk/by-uuid/
```
find your drive and do the same thing you already have in fstab using uuid. It shouldn't change until you format your drive.

Good luck
Aaron

---

### Post by kosmic on 2007-07-05
If you don't want your drives to change wenever you reboot your system can use UUID instead of the name of the Drive.

---

### Post by Beatbreaker on 2007-07-06
> **ggaaron said:**
> Let's assume you have one sata hard drive - it's /dev/sda, now you plug in usbdrive1 - it's /dev/sdb, plug in usbdrive2 - it's sdc, now plug out all usbdrives, plug in usbdrive2 - i't /dev/sdb - it has changed from the last plug in, moreover /dev is known to change drive's names without reason.

What you need to do is:
```
ls -la /dev/disk/by-uuid/
```
find your drive and do the same thing you already have in fstab using uuid. It shouldn't change until you format your drive.

Good luck
Aaron




Thanks for the tips. i've got 2 IDE drives and 3 SATA drives. i tried the uuid code and got this 

```
total 0
drwxr-xr-x 2 root root 220 2007-07-07 02:08 .
drwxr-xr-x 6 root root 120 2007-07-07 12:08 ..
lrwxrwxrwx 1 root root  10 2007-07-07 12:08 045e2f5e-3b5a-45ab-af4b-f0d3480a460b -> ../../hdc5
lrwxrwxrwx 1 root root  10 2007-07-07 12:08 1AC4D576C4D5551B -> ../../hdd1
lrwxrwxrwx 1 root root  10 2007-07-07 12:08 2418A3E918A3B7E6 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-07-07 02:08 2C38B3A038B3678A -> ../../sdc5
lrwxrwxrwx 1 root root  10 2007-07-07 12:08 36B86E6CB86E2A97 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2007-07-07 02:08 9408FEC608FEA680 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2007-07-07 12:08 A8FC1668FC163154 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-07-07 12:08 d5b43a11-d3d3-4ff9-bbf8-17bc2c6f811b -> ../../hdc1
lrwxrwxrwx 1 root root  10 2007-07-07 12:08 DE6CA9076CA8DC11 -> ../../sda2

```


so for example in my fstab in place of the /dev/sda1 i'd put instead UUID=2418A3E918A3B7E6

i'll do a backup and give it a try

---

### Post by Beatbreaker on 2007-07-06
woked perfectly guys, thanks for the valueable tips- consider this one [SOLVED]

---

