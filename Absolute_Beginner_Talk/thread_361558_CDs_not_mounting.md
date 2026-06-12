---
title: "CDs not mounting"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-02-14
I am still having problems playing CDs on my Xubuntu system. I've gone through the Xubuntu guide to multimedia, and downloaded the recommended packages, such as gstreamer, et al. 

When I put the CD in the tray, it just doesn't show up on the desktop, or in any of the media players, or in Thunar, or under CDrom0. The hardware will play CDs in the windows partition. 

I've been going over old threads and googling all evening, and I am feeling a bit frustrated. 

/etc/fstab as follows. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0db92858-50cb-4ec7-8dc5-3dd2678b0769 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=291D-1BDB  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=0b27d919-c88e-45fd-8dea-8805ccb9deaf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

I have tried to mount the CD with sudo mount /dev/hdc: 

brendan@Bell12:~$ sudo mount /dev/hdc
Password:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

brendan@Bell12:~$ dmesg | tail
[17189370.192000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17189370.192000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17189370.192000] ide: failed opcode was: unknown
[17189370.192000] end_request: I/O error, dev hdc, sector 0
[17189370.200000] FAT: unable to read boot sector
[17191155.988000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17191155.988000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17191155.988000] ide: failed opcode was: unknown
[17191155.988000] end_request: I/O error, dev hdc, sector 64
[17191155.988000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

Any suggestions on where to go from here would be greatly appreciated,

---

### Post by tronica on 2007-02-14
for me i just do 

> mount /media/cdrom0

and that works here.

---

### Post by Brendantb on 2007-02-14
Hi, 

That give me the same error message as sudo mount /dev/hdc.

---

### Post by Brendantb on 2007-02-16
I have come across this thread: 

[http://ubuntuforums.org/showthread.php?t=241134](http://ubuntuforums.org/showthread.php?t=241134)

Which deals with exactly the same problem. 

Does anyone know if it was resolved? 

I am going to reinstall Ubuntu on another drive, and see if it works any better.

---

### Post by Brendantb on 2007-02-16
With Ubuntu installed music playing works perfectly. 

A little cd icon appears on the desktop, and then Sound Juicer starts automatically, with a full listing of the CD contents. 

Is this the way it should work with a proper install of Xubuntu?

---

### Post by Brendantb on 2007-02-16
I downloaded Sound Juicer and its dependancies, and CDs now play. 

The only thing I would like now is for SJ to open automatically when I put in a CD, but doubtless there is way to organise that. 

At least the problem is solved.

---

