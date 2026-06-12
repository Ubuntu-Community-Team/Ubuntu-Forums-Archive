---
title: "CD Mount problem"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by laruku_fan on 2007-12-17
Hi! I didn't know where to post this, so here it goes:

My CD/DVD drive keeps mounting an Audio disk, but the problem is that I don't have anything inserted in the drive. I've tried unmounting and ejecting it, but unsuccesfully. 

When I select properties it shows the following:
-Name: Audio Disc
-Type: unknown type
-Size: unknown
-Location: on the desktop
-MIME type: application/octet-stream
-Modified: unknown
-Accesed: unknown

Maybe its because I installed ubuntu on my laptop :confused:
Anyone has an idea on how to fix this? Thanks!

---

### Post by alienexplorers on 2007-12-17
Please post your /etc/fstab file here.

---

### Post by laruku_fan on 2007-12-17
Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c5800480-d266-44b1-a15b-eaccbc9f9372 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d1b0f2f8-5e20-4c6f-88a2-9c3fe7f147c5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

