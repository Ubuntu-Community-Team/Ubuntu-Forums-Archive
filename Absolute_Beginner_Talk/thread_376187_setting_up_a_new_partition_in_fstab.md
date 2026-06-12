---
title: "setting up a new partition in fstab"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by retrodans on 2007-03-04
I have been trying for two weeks now to get this working, and have learnt a lot, but have hit the final stumbling block, as I can't seem to set the priviledge to the disk.

My disk mounts to the desktop, I can open it and look at it's contents, but when I copy a file to it, i receive an error stating:

> "You do not have permissions to write to this folder"

I have tried changing bits, but as I have only recently moved to linux, more often than not it no longer mounts the disk when I ammend stuff.  Below is the code currently in my fstab, the partition I am trying to mount is hdc5

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=b6203fce-752a-434c-946a-1616dfcebe9c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=2884EAE484EAB40A /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=6AFC3D11FC3CD951 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=D258CFCE58CFAF91 /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=d9f24731-6670-4581-b86a-9898cd563247	/media/hdc5	ext3    defaults	0       0
# /dev/hda6
UUID=c57dc3ab-f90c-4740-9b08-36ffe56edece none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1 /mnt/captive-music__76_7gb_ captive-ntfs defaults,noauto 0 0
/dev/hdb1 /mnt/captive-incoming___tosort__114gb_ captive-ntfs defaults,noauto 0 0
/dev/hda1 /mnt/captive-windows captive-ntfs defaults,noauto 0 0

```

Any light you can shed on this problem would be much appreciated!

---

### Post by annda on 2007-03-04
your fstab looks OK.

what are the permissions on the drive?

ls -l /media

if it's not drwxrwxrwx

try

sudo chmod -R 777 /media/hdc5

---

### Post by retrodans on 2007-03-04
Awesome, after a reboot that sorted the problem out fine I don't suppose you could let me know what that was on the screen after listing all the mounts, and also what we did to fix it.  Just so I know for future reference.  Thankyou again for all of your help!

:KS

---

### Post by annda on 2007-03-04
do you mean the sudo chmod... stuff?

lots of info on permissions is here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

it's been typed by some nice people once, so i won't do it again here ;-)

---

### Post by retrodans on 2007-03-04
thankyou very much, that link explains it all perfectly.  Thankyou again for all your help!

---

