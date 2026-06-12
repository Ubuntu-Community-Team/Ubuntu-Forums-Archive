---
title: "How long does Ubuntu take to install?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by The-Master on 2007-01-23
Well I have been waiting for about half an hour now and it is stuck at the install part 5 of 6, Prepare disk space and it seems to have frozen.  I am trying to install an an external drive if that makes any difference and am resizing the drive partition #2 and clicked forward,  Nothing has happened.  Should I restart?

Help:(

EDIT!!  I just closed and installed by deleting everything on the disk but I got an error.  Does anyone know why?  Thanks > The ext3 file system creation in partition #1 of SCSI4 (0,0,0) (sde) failed.

---

### Post by mikewhatever on 2007-01-23
Resizing a partition can take some time. Do not restart, unless you really have to. The time it takes to complete, depends on the structure of that partition.

---

### Post by The-Master on 2007-01-23
> **mikewhatever said:**
> Resizing a partition can take some time. Do not restart, unless you really have to. The time it takes to complete, depends on the structure of that partition.

How long is some time?  Anyway,  I restarted it and am getting that error [COLOR="Red"]The ext3 file system creation in partition #1 of SCSI4 (0,0,0) (sde) failed.[/COLOR] and don't know what is wrong.  Is there anything I can do?  Thanks again:)

---

### Post by lyceum on 2007-01-23
if you are installing on an external drive, it can talk longer, as it is running through a USB or firewire (though firewire may not be too slow)

---

### Post by mikewhatever on 2007-01-23
> **The-Master said:**
> How long is some time?  Anyway,  I restarted it and am getting that error [COLOR="Red"]The ext3 file system creation in partition #1 of SCSI4 (0,0,0) (sde) failed.[/COLOR] and don't know what is wrong.  Is there anything I can do?  Thanks again:)

Unfortunately, there is no fixed time to speak of, but sometimes, it's worth to wait a few minutes longer.

---

### Post by TheWizzard on 2007-01-23
maybe you want to use the gparted live cd to do the partitioning. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

sde looks like an usb disk. is that correct and is this what you want?

---

