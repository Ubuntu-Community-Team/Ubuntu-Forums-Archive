---
title: "Cannot mount volume 2!!!!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2007-09-08
I have very odd bug. When I put DVD with movies in dvd rom some are mounted normal and with some I get this message: Cannot mount volume
Invalid mount option when attempting to mount the volume 'NEW'
I already discuset about this bug: [http://ubuntuforums.org/showthread.php?t=446822](http://ubuntuforums.org/showthread.php?t=446822)
Now I try to edit etc/fstab
I tried using nautilus as root, using terminal and sudo command and on end gksudo. (Using gksudo I started gedit and changed fstab).
Every time I edit etc/fstab it say that I don't have the privileges to mount.
How to edit it that on end works fine?????? :confused:

---

### Post by alienexplorers on 2007-09-08
In the /media directory check the ownership of cdrom0 & cdrom1.  Use the command ls -l in the terminal from within the /media directory.

---

### Post by skymera on 2007-09-08
if need be, try

```
 sudo mount -a
```

---

### Post by _mOrgoth_ on 2007-09-08
Ok... It seams that ubuntu don't  want to mount udf file structure dvd-s. Iso is mounted with no problem. This are my /media and /etc/fstab before changes:

media:
morgoth@krompir:/media$ ls -l
total 12
lrwxrwxrwx 1 root root    6 2007-09-08 14:04 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-09-08 14:04 cdrom0
drwxr-xr-x 2 root root 4096 2007-09-08 14:04 cdrom1
lrwxrwxrwx 1 root root    7 2007-09-08 14:04 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-09-08 14:04 floppy0

etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=69a1f937-1710-4108-b922-e69ac8860298 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6cc54235-a87a-4c34-b63e-d0790180febe none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I found a tip on the net that there should be coma instead space betwean iso9660 and user. So, in terminal I wrote:gksudo gedit fstab, and I put coma there. This is situation after:

media:
morgoth@krompir:/media$ ls -l
total 12
lrwxrwxrwx 1 root root    6 2007-09-08 14:04 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-09-08 14:04 cdrom0
drwxr-xr-x 2 root root 4096 2007-09-08 14:04 cdrom1
lrwxrwxrwx 1 root root    7 2007-09-08 14:04 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-09-08 14:04 floppy0

etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=69a1f937-1710-4108-b922-e69ac8860298 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6cc54235-a87a-4c34-b63e-d0790180febe none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660,user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660,user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

And again... When I put DVD in rom it say: "You are not privileged to mount the volume "...."
:lolflag:

---

### Post by _mOrgoth_ on 2007-09-08
I find the solution on this forum. 
[http://ubuntuforums.org/showthread.php?t=500820&highlight=Cannot+mount+volume+Invalid+option+when+attempting+to+the](http://ubuntuforums.org/showthread.php?t=500820&highlight=Cannot+mount+volume+Invalid+option+when+attempting+to+the)

In etc/fstab instead of "udf,iso9660" should be "auto".

Thx and sry for spaming....

---

