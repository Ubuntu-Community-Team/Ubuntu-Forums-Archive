---
title: "Mozilla won't start re: password access of FAT32 drive"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by unbuntunoob on 2007-05-05
I've set up a dual boot system with XP and Ubuntu. Partitioned ntfs/Fat32 on main drive and use second drive for ubuntu only. Found out that upon boot into ubuntu, firefox and thunderbird both brought up error 'Another version of program already running. Close program or restart' (sorry, can't remember exact error) but I could solve it by accessing my Fat32 drive which brought up request for password. From that point on both programs worked fine.

I've set ubuntu up to mount fat32 drive at boot (didn't include password) and can access the drive but password request does not show up and programs will not start. 

Can anyone tell me what to add for full access when drive mounts at startup?

Thanks

---

### Post by jargoman on 2007-05-05
using feisty this is my setup

partition                                mount point               file type
        
/dev/hda1                             /media/hda1               ntfs                                   (windows xp)
/dev/hda2                             /media/hda2               fat32


/dev/hdb1                             /                                      ext3
/dev/hdb2                             /home                           ext3
/dev/hdb3                             swap                              swap 

I added the /home partition that way if I need to reinstall I keep all my gnome settings and personal files as long as I chose not to format it.

---

### Post by unbuntunoob on 2007-05-05
I'm not sure how I can use the information in your post to help me jargoman. I'll try and give more information this time, I was in a bit of a rush the first post.

Since the first post I have reset fstab to the pre-mount change in order to access firefox.

Current fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=6f920ef9-a2f8-46fa-9f32-a522a33a1657 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=b8a506ab-975e-4f75-9085-99126326cf4b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0

Current fdisk:
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14603   117298566    7  HPFS/NTFS
/dev/hda2           14604       30401   126897435    b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9541    76638051   83  Linux
/dev/hdb2            9542        9729     1510110    5  Extended
/dev/hdb5            9542        9729     1510078+  82  Linux swap / Solaris

I am using hda2 for my Mozilla thunderbird and firefox files so my profiles can be shared in both xp and ubuntu. Access to hda2 from ubuntu needs a password and the neither mozilla program will start without that permission. Unless I can remove the need for password permission (in xp I would assume) the auto mount of hda2 must include that password.

I followed a short tutorial on how to mount hda2 and did so but without adding the password (no instructions on that) after that change I could access the drive but didn't have to enter my password so mozilla still had the same starting problems. The trouble was that the prompt for a password never came up and I could not access mozilla without removing the drive mount command.

I hope this makes my problem a bit clearer.

First time with linux so please bear with me.

---

