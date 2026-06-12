---
title: "Upgraded to Gutsy Gibbon lost ability to mount my second hard d rive"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by jeffkantoku on 2007-12-23
i'm a real beginner, especially when it comes to the command line.  i need help in the form of an exact command to copy and paste and/or alter slightly.

here's a brief history.  i have two NTFS hard drives that i use frequently.  my second NTFS hard drive I used when I used Windows XP, but when it got a virus and after I tried to upgrade to Windows XP Service Pack2 it would crash constantly and never installed properly and I could'nt access my files any more and so I got Ubuntu Feisty Fawn installed on my new hard drive and use my old drive as a secondary storage drive, mainly to acces my old files.   When I had Feisty, I could mount and access my old drive no problem.  it was one of the reasons I switched to Ubuntu.

but when I upgraded to Gutsy I lost the ability to mount the drive.

so I would like to know the commmand line command to force the mount or whatever I have to do.

i believe the drive I'm trying to mount is hdb1.  not sure though.

here"s my info:

jeff@jeff-desktop:~$ sudo fdisk -l

Disk /dev/hda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa28ea28e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30257   243039321    7  HPFS/NTFS
/dev/hda2           30258       60613   243834570   83  Linux
/dev/hda3           60614       60801     1510110    5  Extended
/dev/hda5           60614       60801     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5c2e5c2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       16708   134206978+   7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4bda4bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241    c  W95 FAT32 (LBA)
jeff@jeff-desktop:~$

jeff@jeff-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=5c623900-ee80-489d-92e1-f9efa3d97a46 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b00daa25-3d12-4e11-8229-9c136cbacc6e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
jeff@jeff-desktop:~$ 

looking for any help!  Thanks guys, I'm counting on you!

---

### Post by spiderbatdad on 2007-12-23
i can tell you'll understand these instructions;)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jeffkantoku on 2007-12-23
this is what i get when I try to edit fstab

i dont think it has the drive I want listed.  I think I want hdb1.


 GNU nano 2.0.6              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=5c623900-ee80-489d-92e1-f9efa3d97a46 /               ext3    defaults,erro$
# /dev/hda5
UUID=b00daa25-3d12-4e11-8229-9c136cbacc6e none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by logos34 on 2007-12-24
The psychocats page is self-explanatory.  However it would probably be easier to use [ntfs-config]("https://help.ubuntu.com/community/MountingWindowsPartitions#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971")--it will edit fstab for you and hdb1 will even mount with write-acess.

For the sda1 fat32 partition, manually add this line:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda2
UUID=5c623900-ee80-489d-92e1-f9efa3d97a46 / ext3 defaults,erro$
# /dev/hda5
UUID=b00daa25-3d12-4e11-8229-9c136cbacc6e none swap sw $
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
[COLOR="Blue"]/dev/sda1 /media/sda1 vfat iocharset=utf8,umask=000 0 0[/COLOR]
If the mount point doesn't exist, remember to create it:
[B]
sudo mkdir /media/sda1[/B]

*Note: if you want to use UUID format, you can find them with 
[B]
blkid[/B]

or 
[B]
ls -l /dev/disk/by-uuid[/B]

---

