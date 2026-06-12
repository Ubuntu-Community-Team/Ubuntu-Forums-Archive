---
title: "CD / DVD RW can't mount"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by KillerSiafu on 2007-08-04
I'm running 7.04 on a dell 1420 N laptop, 2.0 Ghz Duo Intel t7300 chip, 2 gb's of ram, SATA 160gb 7200 RPM harddrive.

When I first got the machine on a clean ubuntu install I was able to read cd's / dvd's no problem. Since the clean install, I've tried installing some applications / extras (such as beryl, which i've now uninstalled), and now I'm unable to mount my cd / dvd rw drive. I currently have the ubuntu cd in the drive, which is recognized on boot, but not once ubuntu loads. When I try and access the drive I get the following error:

[INDENT]Unable to mount the selected drive
mount: special device /dev/scd0 does not exist

[/INDENT]

My fstab looks like:

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1631bfef-4fa7-422c-9620-d325d54781bf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2d66bb8e-2902-40c1-9027-e7f91838d481 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=8cc2dafe-fdff-44b6-bb3b-aa9d9f92681f  /boot ext3 defaults 0 0
[/INDENT]

My lsusb looks like:

[INDENT]Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 413c:8126 Dell Computer Corp. 
Bus 001 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 008: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 009: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 [/INDENT]

I've tried doing a mount like:

```
sudo mount -t iso9660 /dev/scd0/media/cdrom0
```

But that doesn't seem to work either...

Anyone have any suggestions?

---

### Post by tbroderick on 2007-08-05
Have you tried
```

sudo mount -t iso9660 /media/cdrom0
```

---

### Post by KillerSiafu on 2007-08-05
tbroderick...

No luck. I get the whole how to use mount description, same as before.

---

### Post by tbroderick on 2007-08-05
What's listed under /media and can you post the output of dmesg?

---

### Post by KillerSiafu on 2007-08-05
In the media directory there are

cdrom    cdrom0


The dmesg is pretty long so I attached it

---

### Post by Arjent on 2007-08-05
I had exactly the same problem and after a lot of forum scouring I found a solution that worked.
Try going into your boot sequence and altering the order so your cdrom boots after your hard drive.  It worked for me and a few others.

Good luck

---

