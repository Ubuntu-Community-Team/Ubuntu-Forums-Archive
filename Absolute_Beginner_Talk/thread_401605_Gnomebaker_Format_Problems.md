---
title: "Gnomebaker Format Problems"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by gerrymoth on 2007-04-04
I've installed gnomebaker, but every time I try to blank the DVD +RW by doing a 'Format DVD +-RW' I get the following message:

> * BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
umount: /media/My Disc is not in the fstab (and you are not root)
:-( unable to proceed with format: Device or resource busy<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by LaurelLynn on 2007-04-04
Dear gerrymoth,

From a terminal type:

cat /etc/fstab

It will list all the drives that are mountable on your system (in fact mount/umount won´t work unless  there is an entry here first).

There should be an entry like:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

If not you can try editting the file (sudo gedit /etc/fstab), and adding it. If you have several drives there may  already be an entry with ¨/dev/hdc¨, in which case the cdrom will be hd some other letter.

Then:

sudo mount   /media/cdrom0

If it still doesn´t work I would try uninstalling Gnomebaker  Reboot reinstall.

Laurel Lynn

---

### Post by gerrymoth on 2007-04-05
> **LaurelLynn said:**
> Dear gerrymoth,

From a terminal type:

cat /etc/fstab

It will list all the drives that are mountable on your system (in fact mount/umount won´t work unless  there is an entry here first).

There should be an entry like:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

If not you can try editting the file (sudo gedit /etc/fstab), and adding it. If you have several drives there may  already be an entry with ¨/dev/hdc¨, in which case the cdrom will be hd some other letter.

Then:

sudo mount   /media/cdrom0

If it still doesn´t work I would try uninstalling Gnomebaker  Reboot reinstall.

Laurel Lynn

Thanks LaurelLynn,

Noticed when I did a fstab that my cdrom0 is /dev/hdb, but it is mounted to /media/cdrom0.
Trying to find a good tutorial or step by step guide to mounting partitions as I'm getting a bit confused.

Here's what I've got:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 510 4096543+ 12 Compaq diagnostics
/dev/sda2 * 511 3871 26997232+ c W95 FAT32 (LBA)
/dev/sda3 3872 5852 15912382+ c W95 FAT32 (LBA)
/dev/sda4 5853 7296 11598930 5 Extended
/dev/sda5 * 5853 7233 11092851 83 Linux
/dev/sda6 7234 7296 506016 82 Linux swap / Solaris

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda5
UUID=a1d94cc5-ef28-4f83-9f6a-f4b2e3a328e5 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6
UUID=38c4e3c4-83de-4690-b9b1-e699fbe606c9 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by LaurelLynn on 2007-04-05
It looks like your on an SATA drive like me.

Try this command:

ls /dev/h*

there should be only a few entries I have:

hdc  hpet

I don´t know what ¨hpet¨ is but drives always start hd so hdc must be my cdrom.

cat /etc/fstab

Yields:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

fstab tells Ubuntu how to match a device driver with a mount directory. So the  /dev/hdc  matches up. Your cdrom drive definitely needs an fstab entry that matches the correct  /dev  devicer driver before it can be mounted.

next:

ls /media

If there isn´t a cdrom0 entry I would try ¨sudo mkdir /media/cdrom0¨ before mounting the cdrom drive.


I think your loosing the drive somewhere in that chain.

Laurel Lynn

---

### Post by gerrymoth on 2007-04-05
Thanks for the reply, I'm at work just now so will try tonight, also did so searching and found these two websites which maybe of help to me:

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

---

