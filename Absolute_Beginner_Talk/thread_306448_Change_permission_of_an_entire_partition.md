---
title: "Change permission of an entire partition?"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2006-11-25
My /home partition has filled up, so I want to transfer files to another ext3 partition that mounts at startup (hdb6).

I can't right-click and create folders on that partition.   How do I change permissions so I have full read/write access to that partition?

Thanks in advance..

---

### Post by aysiu on 2006-11-25
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) should help.

---

### Post by wilberfan on 2006-11-26
Hmmm... Based on that tutorial, I did the following, but still can't right-click and create a folder ...

```
sudo chown -R me:me /media/hdb6
sudo chmod -R 755 /media/hdb6
```

When I right-click on the hdb6 icon on the desktop and look at "properties" it still says that 'root' is the owner...

Did I miss something...?

---

### Post by wilberfan on 2006-11-26
Well, I rebooted, and everything seems fine...    Is rebooting (or maybe remounting that partition??) necessary in this scenario?

---

### Post by aysiu on 2006-11-26
[quote=wilberfan]Well, I rebooted, and everything seems fine... Is rebooting (or maybe remounting that partition??) necessary in this scenario?[/quote] Shouldn't be necessary. A simple ```
sudo mount -a
``` after editing the /etc/fstab should do it, but a reboot never hurts.

---

### Post by wilberfan on 2006-11-26
> **aysiu said:**
> Shouldn't be necessary. A simple ```
sudo mount -a
``` after editing the /etc/fstab should do it, but a reboot never hurts.

This is what I get when I try a "sudo mount -a" command:

> Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Failed to mount '/dev/disk/by-uuid/1864CF6A64CF48E8': Device or resource busy
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Failed to mount '/dev/disk/by-uuid/418052E87E1851AA': Device or resource busy
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Failed to mount '/dev/disk/by-uuid/26C4BF71C4BF423B': Device or resource busy
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

:o

---

### Post by taurus on 2006-11-26
What does your /etc/fstab look like again?

```
cat /etc/fstab
```

---

### Post by wilberfan on 2006-11-26
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=9a7c8ff9-3b35-4792-abab-17357f474c60 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=9a0d8b8c-0e16-4782-8e24-628009ad14b2 /home           ext3    defaults        0       2
# /dev/hda1
UUID=1864CF6A64CF48E8 /media/hda1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=418052E87E1851AA /media/hda4     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=26C4BF71C4BF423B /media/hda7     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
#
#
# /dev/hdb1
/dev/hdb1 /media/hdb1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
#
# /dev/hdb2
#UUID=2c608213-7f8e-4b08-9a2a-8e44846cf364 /media/hdb2     ext3    defaults        0       2
#
# /dev/hdb6
/dev/hdb6 /media/hdb6     ext3    defaults        0       0
#
# /dev/hdb5
/dev/hdb5 /media/hdb5     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
#
# /dev/hdb7
/dev/hdb7 /media/hdb7     vfat    defaults,utf8,umask=007,gid=46 0       1
#
# /dev/hda5
UUID=ac586b0c-5754-4144-869d-a4bc0d2fef1f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

Ohhh.....yer gonna say sumthin' about ntfs-3g, arentcha?!  ;)

---

### Post by taurus on 2006-11-26
For both vfat and ntfs-3g in your /etc/fstab, the last two numbers should be "0 0" not "0 1"...

---

### Post by wilberfan on 2006-11-26
> **taurus said:**
> For both vfat and ntfs-3g in your /etc/fstab, the last two numbers should be "0 0" not "0 1"...
*Really?!*

That's *very* good to know--thanks!!   BTW, can you tell me what those numbers represent?   They're what would have been set up when I installed Ubuntu...

---

### Post by wilberfan on 2006-11-26
> **taurus said:**
> For both vfat and ntfs-3g in your /etc/fstab, the last two numbers should be "0 0" not "0 1"...

I notice the ext3's are "0 2"... they're OK like that?

---

