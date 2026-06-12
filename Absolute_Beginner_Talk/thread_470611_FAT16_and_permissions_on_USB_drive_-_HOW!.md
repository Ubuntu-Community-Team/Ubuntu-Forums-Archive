---
title: "FAT16 and permissions on USB drive - HOW?!"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Outrunner on 2007-06-11
Hello everyone,

What I'm trying to do is make a LiveUSB + persistence mode out of a Dapper .iso. So far it's going well... Except for the part that I don't have permission to write to my usb drive. I've done this before with Knoppix and I didn't have this problem, but admittedly, I've done it in a different environment(from the LiveCD). 

Funny thing is, I can copy some directories(casper, disctree etc) but others, I can't copy their contents(dists/dapper/ is being copied but dists/stable/ and dists/unstable/ say I don't have permission). Anyway:

```

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          46      369463+  82  Linux swap / Solaris
/dev/sda2              47       14946   119684250    5  Extended
/dev/sda5              47         821     6225156   83  Linux
/dev/sda6             822        6754    47656791   83  Linux
/dev/sda7            6755       14946    65802208+  83  Linux

Disk /dev/sdb: 2029 MB, 2029518848 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         104      835348+   6  FAT16
/dev/sdb2             105         246     1140615   83  Linux

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=00b946cf-6c5d-4bcf-83ea-8b8411e1c55c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=8f795da3-834e-47ae-a16f-d63c063cc74e /home           ext3    defaults        0       2
# /dev/sda5
UUID=f8286a5f-3f7f-4c21-8464-123fd3012575 /meta           ext3    defaults        0       2
# /dev/sdb1
/dev/sdb1  /usb            vfat iocharset=utf8,umask=000 0 0
# /dev/sda1
UUID=67c64dc8-f174-4527-a5cb-e7a509805c57 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

With the options I set, isn't it supposed to work? Drivin' me crazy!!

EDIT: Forgot to mention, I'm using Kubuntu Gutsy(Tribe 1) on this computer, if this is of any importance

---

### Post by ggaaron on 2007-06-11
I had similar problem on ubuntu before - reformating drive helped. But before you do it try this (i don't know if it will help, I can't check now, but possibly...) run a terminal:

```

sudo su
chmod 0777 /usb
chown (place your username here) /usb
mount /usb
chmod 0777 /usb
chown (place your username here) /usb

```

It helped me, when I couldn't mount my drives as a normal user (and I had user option in fstab)

you may also change group with chgrp if you want.

---

### Post by Outrunner on 2007-06-12
Well, the FAT filesystem doesn't have the same permission system, so that won't work. I tried it.

---

### Post by ggaaron on 2007-06-12
That's bad=/ I knew that fat is different - I believe no owner and group setting, I could have thought before posting that there was small chance of it working=/

---

### Post by timcredible on 2007-06-12
if you want file permissions, you need to use a filesystem that supports them, like ext3.  just format your drive as ext3, and you should be ok.  gparted will do that easily.  if you need to keep some of the drive accessible for windows, partition some of the drive as ext3 and leave some of it as fat16.  as a side note, you do the same things with flash drives.

---

### Post by ggaaron on 2007-06-12
In fact I've seen excellent ext3 drivers for windows - you install it and your drive acts just as any other fat/ntfs drive. So if you use it only on your machines then ext3 can be quite a nice option.

---

### Post by Outrunner on 2007-06-12
Does anyone have a solution besides reformatting? I know it can work, since I had Knoppix on this very drive some time ago...

---

