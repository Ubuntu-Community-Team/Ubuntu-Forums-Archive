---
title: "Fat32 Partitions. Just noticed"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-05-04
I just noticed that those FAT32 partitions I created on my extra internal HD only have root permissions. I can read, but I cannot write. How do I give them user permissions?

---

### Post by aysiu on 2006-05-04
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by georgetoon on 2006-05-04
I just noticed again (Duh! dummy me!) I have full read and write permissions for Owner, Group and others.

I can read and write to the drive. Problem is, I can't save a playlist with amarok to these drives.  I gues I jumped to conclusions.  I'm confused.  why can't I save a playlist?

EDIT -- Nope..i'm wrong again.  I just noticed that I cannot write to certain folders.  they have a small lock on them. these folders were created in Windows and used in Linspire. Would I need to enable(give them user permission them in some way in Linspire or Windows?  Because not all folders are locked.

---

### Post by aysiu on 2006-05-04
Can you post the output of this terminal command? ```
cat /etc/fstab
```

---

### Post by georgetoon on 2006-05-04
[QUOTE=aysiu]Can you post the output of this terminal command? ```
cat /etc/fstab
```[/QUOTE]

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/hdd1 /fat1 vfat iocharset=utf8,umask=000 0
/dev/hdd5 /fat2 vfat iocharset=utf8,umask=000 0
/dev/hdd6 /fat3 vfat iocharset=utf8,umask=000 0
/dev/hdd7 /fat4 vfat iocharset=utf8,umask=000 0
/dev/hdd8 /fat5 vfat iocharset=utf8,umask=000 0
/dev/hdd9 /fat6 vfat iocharset=utf8,umask=000 0

---

### Post by aysiu on 2006-05-04
Hm. Looks good to me.

The only thing I could think of is that sometimes putting the mount point inside of /media or /mnt messes up the permissions, but you have the mount points in their own static directories.

I'm stumped.

---

### Post by georgetoon on 2006-05-04
[QUOTE=aysiu]Hm. Looks good to me.

The only thing I could think of is that sometimes putting the mount point inside of /media or /mnt messes up the permissions, but you have the mount points in their own static directories.

I'm stumped.[/QUOTE]

I appreciate you taking a look.:)

---

### Post by nanotube on 2006-05-05
hi
try changing your vfat lines to the following:
```
/dev/hdd1 /fat1 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd5 /fat2 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd6 /fat3 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd7 /fat4 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd8 /fat5 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd9 /fat6 vfat iocharset=utf8,umask=000,uid=1000 0 0
```
the last 0 i added there is not that important (but should be there for good form). the important part is the uid bit - it mounts the files so that your user is the owner, rather than root. that ought to help you out some. (by default your uid should be 1000 - but check to make sure by running command "id" from a terminal)

---

### Post by georgetoon on 2006-05-05
[QUOTE=nanotube]hi
try changing your vfat lines to the following:
```
/dev/hdd1 /fat1 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd5 /fat2 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd6 /fat3 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd7 /fat4 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd8 /fat5 vfat iocharset=utf8,umask=000,uid=1000 0 0
/dev/hdd9 /fat6 vfat iocharset=utf8,umask=000,uid=1000 0 0
```
the last 0 i added there is not that important (but should be there for good form). the important part is the uid bit - it mounts the files so that your user is the owner, rather than root. that ought to help you out some. (by default your uid should be 1000 - but check to make sure by running command "id" from a terminal)[/QUOTE]

Thanks.:)  I'll give that a shot.:)  I'm also thinking that maybe I simply need to pop in Linspire and change the permissions on theose folders?  In Linspire, I run as root (okay, okay, no yelling at me, please.:)), and maybe I just need to change these through Linspire?

---

### Post by nanotube on 2006-05-05
well, fat32 does not really even support permissions on files - so i am not sure what's going on. maybe linspire is using some kind of hacky thing to make permissions. i suppose it doesnt hurt to try changing permissions through linspire and see if that does anything. :)

---

### Post by georgetoon on 2006-05-05
[QUOTE=nanotube]well, fat32 does not really even support permissions on files - so i am not sure what's going on. maybe linspire is using some kind of hacky thing to make permissions. i suppose it doesnt hurt to try changing permissions through linspire and see if that does anything. :)[/QUOTE]

Well, yep that was the problem. I went into Linspire, found the advanced permissions, toggled them on, Jumped into Ubuntu and the folders can now be read and written!:)

---

### Post by nanotube on 2006-05-06
cool, glad it worked. i do wonder what kind of fancy disk-foo linspire does to make permissions on fat32...

---

