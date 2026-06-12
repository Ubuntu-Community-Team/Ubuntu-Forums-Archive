---
title: "/etc/fstab issue"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Big Fish on 2007-04-10
I'm trying to mount my two DVD drives in Edgy. This is my current /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system>		<mount point>   <type>		<options>			<dump>  <pass>
proc			/proc		proc		defaults			0	0
/dev/hda1		/		ext3		defaults,errors=remount-ro	0	1
/dev/hda5		none		swap		sw				0	0
/dev/hdc1		/backup		ext3		defaults			0	0
/dev/hdb		/media/dvd1	udf,iso9660	defaults,noauto,user,ro		0	0
/dev/hdd		/media/dvd2	udf,iso9660	defaults,noauto,user,ro		0	0
```

I have two folders in /media named "dvd1" and "dvd2".

What am I doing wrong???

---

### Post by devnulljp on 2007-04-11
Can you mount manually using sudo mount /media/dvd1 ?
You sure those devices are where your drives are? They're on your ide bus and not usb or scsi?
Can you try:
/dev/hdb        /media/dvd1   udf,iso9660 user,unhide,noauto     0       0
/dev/hdd        /media/dvd2   udf,iso9660 user,unhide,noauto     0       0

---

### Post by Big Fish on 2007-04-11
When I do "sudo mount /media/dvd1" with a data dvd in the bottom drive, it works fine.
When I do "sudo mount /media/dvd2" with a data dvd in the top drive, it says "no medium found".
I didn't make any changes to the /etc/fstab file yet (same as first post).

When I do "sudo mount -ls", I get this:
/dev/hdb on /media/dvd1 type iso9660 (ro,noexec,nosuid,nodev) [backup081406]
There's nothing about /dev/hdd anywhere.

---

### Post by Big Fish on 2007-04-11
I just checked the devices within GnomeBaker and it recognizes both drives. Although, when I try to format a DVD+RW in the drive, it says:

* DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 6.1.
:-( mounted media doesn't appear to be DVDÂ±RW or DVD-RAM

---

### Post by NICU on 2007-04-11
Hi, an easy way to check what your PC thinks your DVD drive is, is to open device manager, then go to your IDE controller (or ATA or SCSI depending on your system).  In there you can find every individual drive.  Go to the Advanced tab and look at the "block.device" setting.  That's a good place to start so you know where the system is putting your drive.

---

### Post by Big Fish on 2007-04-12
It looks right - /dev/hdd

---

