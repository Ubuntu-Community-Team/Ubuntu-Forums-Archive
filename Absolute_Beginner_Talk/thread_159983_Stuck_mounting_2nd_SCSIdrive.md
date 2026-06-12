---
title: "Stuck mounting 2nd SCSIdrive"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by zorlab on 2006-04-13
[B]
I partitioned drive with Ubauntu cd followed instructions in another post and edited /etc/fstab[/B]
....................................................................................................
[COLOR="Blue"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1[/COLOR]
.....................................................................................................

[B]You can see above that I simplyc opied drive 1 info for sda2...
 then I tried to mount drive after saving fstab[/B]
......................................................................................................
[COLOR="Blue"]root@SCSI:/# mount /dev/sda2
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/COLOR]
**NEXT**
[COLOR="Blue"]root@SCSI:/# dmesg | tail
[4294743.173000] Bluetooth: HCI device and connection manager initialized
[4294743.173000] Bluetooth: HCI socket layer initialized
[4294743.232000] Bluetooth: L2CAP ver 2.7
[4294743.232000] Bluetooth: L2CAP socket layer initialized
[4294743.278000] Bluetooth: RFCOMM ver 1.5
[4294743.278000] Bluetooth: RFCOMM socket layer initialized
[4294743.278000] Bluetooth: RFCOMM TTY layer initialized
[4294836.521000] attempt to access beyond end of device
[4294836.521000] sda2: rw=0, want=4, limit=2
[4294836.521000] EXT3-fs: unable to read superblock[/COLOR]
........................................................................................................

**What do I do here?**

---

### Post by Sutekh on 2006-04-13
[quote=zorlab]```
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
...
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
```[/quote]
Firstly I don't understand why you have two entries in the fstab that are trying to mount to /.

Also the error suggests that /dev/sda2 is an extended partition. 

Are you sure that /dev/sda2 is the corerct location.  Can you provide the output from ```
sudo fdisk -l
```

---

### Post by zorlab on 2006-04-13
Yep... problem solved, named 2nd drive wrong,  should be  **sdb1**

Now I can see the disk in Disk Manager  :D 
So to acces drive do I need to go  to /dev/sdb1  or is there a simple GUI method?

---

### Post by Sutekh on 2006-04-13
I still don't know why you have two partitions mounted to /

To browse just open the file browser (Nautilus) from the Applications -> Accessories menu.  /  is the root filesystem, the highest directory in your filesystem.

---

### Post by zorlab on 2006-04-13
ok I can get to filesystem.....  but  where>???  
As to the  mounting, could you please make a sugestion 

you said "two entries in the fstab that are trying to mount to /."  I put in  the 
'where to mount', I guess,since I don't know what I am doing...... what should it read??](*,)

---

### Post by Sutekh on 2006-04-13
Ok no problem.  The /etc/fstab contains the mounting information.

The first part - /dev/sda1 - is the location of the partition.  The device is a SCSI drive, named sda and the partition is the first one on the disc, hence /dev/sda1.

The second part / is the folder where the partition is mounted to.  /  is the root filesystem of Linux, its probably not a good idea to mount it there.

A good explanation of the fstab can be found here

[TuxFiles.org - How to edit and understand the /etc/fstab](www.tuxfiles.org/linuxhelp/fstab.html)


Here's my suggestion.  Oh and I should ask now, is the partition ext3 or some other format (NTFS/FAT)?  This is important.  If it is formatted ext3, then continue, otherwise let me know what the format is

Unmount /dev/sdb1
```
sudo unmount /dev/sdb1
```
create a folder for it
```
sudo mkdir /media/sdb1
```
Edit the fstab to have this line
```
/dev/sdb1   /media/sdb1   ext3   defaults   0   0
```
Then remount the partition
```
sudo mount -a
```

---

### Post by zorlab on 2006-04-13
Thanks so much,   I am finding that there are so many ways to accomplish via different commands.

Fortunately I gleaned from your previous posts that I must name a dir and change the fstat and then remount. that did the trick!  Idid not, however unmount the device first......

hope this causes no problems.......  [COLOR="red"]I guess it was not actually mounted since the location was a duplicate ??[/COLOR]


Anyway  thanks a bunch for your patience and explanation  8) :D

---

