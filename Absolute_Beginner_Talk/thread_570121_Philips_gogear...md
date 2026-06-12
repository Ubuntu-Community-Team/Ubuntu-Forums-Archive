---
title: "Philips gogear.."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-10-07
hey does any1 have idea about this device gogear.. how do i useit on ubuntu..

---

### Post by cameronw on 2007-10-09
I have a GoGear and I just plug it in and open it in Banshee or File Browser and all my music's there. Does yours need some sort of software to run (windows only software maybe?)

---

### Post by dhani99 on 2007-10-14
noo.. I can't see this device when i plug it.. and i don't think that it needs software.. btw it is HDD 1830

---

### Post by dhani99 on 2007-10-14
is there any way to mount it ? something like media/usb :confused:

---

### Post by cameronw on 2007-10-14
Try: ```
sudo mount /dev/sda /media/usb -t vfat -o umask=0
```If that doesnt work, post your fstab with: ```
cat /etc/fstab
```

---

### Post by dhani99 on 2007-10-14
> sudo mount /dev/sda /media/usb -t vfat -o umask=0

that didn't work..
-------------------------------------------------

keval@desktop ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c4dc3759-b2cf-45e9-a304-e9d03f958639 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=bce6f62b-bdc7-4cd4-b7e6-09d0a7d367f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by dhani99 on 2007-10-14
I do see that device in Hardware info..

---

### Post by lexarrow on 2007-10-15
it didn't work for me either, but I found where it lies:
```
~$ sudo mount /dev/libmtp-usbdev2.13 /media/gogear -t vfat -o umask=0
mount: /dev/bus/usb/002/013 is not a block device

```

I think we have to wait until the next version of libmtp

Another thing, when I plug my gogear in, Rhapsody pops up but when I try to enable the MTP plugin it quits automatically.

Any other ideas?

---

### Post by lexarrow on 2007-10-15
When trying to use mtp-detect I got this error:
```
alex@alex-laptop:~$ mtp-detect
libmtp version: 0.2.1

Attempting to connect device(s)
Potential MTP Device with VendorID:0471 and ProductID:014c responded to control message 2 with a response that was too short. Problems may arrise but continuing
usb_claim_interface(): No such file or directory
LIBMTP PANIC: Unable to initialize device 1
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting
alex@alex-laptop:~$ mtp-detect
libmtp version: 0.2.1

Attempting to connect device(s)
Potential MTP Device with VendorID:0471 and ProductID:014c responded to control message 2 with a response that was too short. Problems may arrise but continuing
usb_claim_interface(): No such file or directory
LIBMTP PANIC: Unable to initialize device 1
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting

```

---

### Post by dhani99 on 2007-10-17
bump ... any1 ??

---

### Post by dhani99 on 2007-10-19
:confused::(

---

### Post by dhani99 on 2007-12-01
:(.. Please..

---

### Post by jonnylentilbean on 2008-05-22
I have a Philips gogear HDD82/17

My problem was that it would recognize in Kubuntu/Ubuntu, but as a camera rather than an mp3 player, and thus I could not view the mp3 files.

My solution was to install gnomad 

sudo apt-get install gnomad

I have no idea how this MIRACLE software works, but it worked like a charm! It automatically recognized my mp3 player, auto-loaded the contents with no configuration, and allowed simple drag/drop/deletion to and from the player. It even has automatic music file detection so i'm not always bothered about transferring non-music files as I get in windows when dragging/dropping.

Hope that helps! I've had this problem for MONTHS and am finally windows-free.

---

