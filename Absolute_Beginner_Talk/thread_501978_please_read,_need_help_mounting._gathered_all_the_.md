---
title: "please read, need help mounting. gathered all the information i could..."
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by redtendoned on 2007-07-16
Ok so my 80 GB Seagate external harddrive is being read just fine. I installed QTParted and rounded up some information.

sdbl (71.31 GB)
Number | 01
Partition | /dev/sdbl
Type | fat32
Status | Active
Size | 74.53 GB
Used space | 71.31 GB
Start | 0.03 MB
End | 74;53 GB
Label | SEA_DISK

Drive Info:
Device: /dev/sdb
Model: ST380011 A
Capacity (Mb): 76319.1
Length sectors: 156301488
Status: available.

It's showing as active, yet it is nowhere to be found in my Places? How do I go about mounting this drive? All my music and course work is on this external and I'd like to be able to access it ASAP. 

Thanks in advance!
-Chris

---

### Post by dpar on 2007-07-16
Does it show up if you go to Places>Computer?

---

### Post by redtendoned on 2007-07-16
No sir, which is why I'm rather confused. Is there anything I should be entering into the terminal to actually mount the device? Sorry if I sound ignorant (it's because I am), just installed Ubuntu late this evening for the first time after many years of Windows/Mac use.

---

### Post by AlexenderReez on 2007-07-16
for me fat32 disk will auto mount itself...but if it still failed...you can always mount with

creating any place like

> sudo mkdir /mnt/music

> sudo mount dev/sdb1 /mnt/music

---

### Post by dpar on 2007-07-16
I'm a little ignorant on that myself.....I'll have to search around for a bit. Meanwhile I'm sure someone smarter will jump in.:)

Edit: See, there ya go....lol

---

### Post by Frak on 2007-07-16
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by redtendoned on 2007-07-16
reez:

"mount: you must specify the filesystem type"

can you verify that command you just gave me?

---

### Post by Ripfox on 2007-07-16
Automatix has a utility that you can get called "Automatix Mounter"

Just download and install Automatix and its under Misc.

---

### Post by HermanAB on 2007-07-16
$ man mount

-t vfstype
              The  argument following the -t is used to indicate the file sys&#8208;
              tem type.  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  coda, coherent, cramfs, devpts,
              efs, ext, ext2, ext3, hfs, hpfs,  iso9660,  jfs,  minix,  msdos,
              ncpfs,  nfs,  nfs4,  ntfs,  proc,  qnx4, ramfs, reiserfs, romfs,
              smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat,  xenix,  xfs,
              xiafs.   Note  that  coherent, sysv and xenix are equivalent and
              that xenix and coherent will be removed at  some  point  in  the
              future — use sysv instead. Since kernel version 2.1.21 the types
              ext and xiafs do not exist anymore. Earlier, usbfs was known  as
              usbdevfs.

So, do this:
$ sudo mount -t vfat /dev/sdb1 /mnt/music

Don't be afraid to read man pages.  Some are bloody terrible, but others are quite good.  

Cheers,

Herman

---

### Post by redtendoned on 2007-07-16
Unbelievable, within ten minutes you guys had me up and running. What an amazing community, thank you all so much!

Now for the eyecandy ;)

Cheers!
-Chris

---

### Post by HabbitSHardin on 2007-07-17
Now that you have it up and running, you should think if you can profit from a bit of automation. Concretely, you can add the partition to /etc/fstab so that it is automagically mounted on boot and/or appears on your "Computer" menu - or so I think xD...

Add a line like this to your /etc/fstab (you need to open it with root access, that is, with sudo nano /etc/fstab):
```
/dev/sdb1    /mnt/music    vfat    defaults,users,umask=007      0      0
```
You can play around with that mount options if you like. Now, if your external drive is connected on boot, it will start mounted. If it is not, I don't know if it will be automounted on insertion but even in the worst case (it is not and doesn't even appear in "Computer"), you can mount it with just ```
mount /mnt/music
```
If your external drive does not always appear as sdb (i.e. might appear as sdc or sdd depending on the USB/FW/eSATA port you use), you might still use the fstab procedure, by replacing the first field (/dev/sdb1) by an UUID by running the "sudo vol_id" command on it:
```
 $sudo vol_id /dev/sdb1
(...)
ID_FS_UUID=cfedf05f-87ff-43dd-8c90-3f847fe29771
(...)
```
The first field in the fstab line should then look like "UUID=cfedf05f-87ff-43dd-8c90-3f847fe29771" (without the quotes).

Have fun!! :popcorn:

---

### Post by Frak on 2007-07-17
instead of using nano, use

gksudo gedit /etc/fstab for gnome or XFCE

kdesu kate /etc/fstab for KDE

---

### Post by AlexenderReez on 2007-07-17
> **HermanAB said:**
> $ man mount

-t vfstype
              The  argument following the -t is used to indicate the file sys&#8208;
              tem type.  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  coda, coherent, cramfs, devpts,
              efs, ext, ext2, ext3, hfs, hpfs,  iso9660,  jfs,  minix,  msdos,
              ncpfs,  nfs,  nfs4,  ntfs,  proc,  qnx4, ramfs, reiserfs, romfs,
              smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat,  xenix,  xfs,
              xiafs.   Note  that  coherent, sysv and xenix are equivalent and
              that xenix and coherent will be removed at  some  point  in  the
              future — use sysv instead. Since kernel version 2.1.21 the types
              ext and xiafs do not exist anymore. Earlier, usbfs was known  as
              usbdevfs.

So, do this:
$ sudo mount -t vfat /dev/sdb1 /mnt/music

Don't be afraid to read man pages.  Some are bloody terrible, but others are quite good.  

Cheers,

Herman

> **redtendoned said:**
> reez:

"mount: you must specify the filesystem type"

can you verify that command you just gave me?

hm...no need... usually user don't specific fat and etc file system.....

but like ntfs use difference system mount so need to specific the case.....hm...because it is all access system....like this mount ---> [http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)

mount ext3 ...

:)

---

