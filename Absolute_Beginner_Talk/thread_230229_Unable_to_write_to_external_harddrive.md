---
title: "Unable to write to external harddrive"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by aliasbs on 2006-08-05
I need to write to my old external harddrive but it displays a "Error while copying to "/media/ieee1394disk".

This harddrive was used by my windows OS for external data, but i cant seem to get it to write with unbuntu.

Is there a way to write to this drive?

---

### Post by taurus on 2006-08-05
Do you mount that drive with /etc/fstab?  If you are, what does your /etc/fstab look like than (from a terminal, Applications -> Accessories -> Terminmal)?

```

more /etc/fstab

```

---

### Post by aliasbs on 2006-08-05
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2006-08-05
How do you mount it because it's not in your /etc/fstab???

---

### Post by aliasbs on 2006-08-05
Im not sure it is mounted correctly

I tried 

mount /media/ieee1394disk

and it returned:

mount: according to mtab, /dev/sdb1 is already mounted on /media/ieee1394disk
mount failed

the mount command displays:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=bsitty)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid =1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdb1 on /media/ieee1394disk type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,um ask=077,iocharset=utf8)

---

### Post by annda on 2006-08-05
external drives are not in /etc/fstab but are mounted dynamically as they are plugged in.

type in the terminal:
```
mount
```
to see if it's not an NTFS drive (it probably is). in that case you can't write to it, only read. (well, actually you can using some gimmicks, but it's not very safe).

search the wiki or forums for 'ntfs' to get you further.

good luck.

[EDIT] you were faster. from your last post - yes, it is NTFS.

---

### Post by iammeagain on 2006-08-05
if you just wanna write things too it then format it to something else.

---

### Post by orb9220 on 2006-08-05
Well you have a choice if you want to be abled to use the drive for xp and linux then use fat32.

you can use gpart for the partitioning and fornatting.

Do you have stuff to get off it first?

---

