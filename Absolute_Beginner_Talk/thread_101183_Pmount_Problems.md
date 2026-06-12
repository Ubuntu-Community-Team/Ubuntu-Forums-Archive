---
title: "Pmount Problems"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-12-09
Having trouble mounting CDs

Error:
Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: No medium found
Error: could not execute pmount

mtab settings:
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0


fstab settings:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom   auto,udf,iso9660 user     0      0

---

### Post by yapsuper on 2005-12-11
What happens when you type this into the terminal```
cat /etc/sysconfig/hwconf
```

---

### Post by sandy_marshall on 2005-12-21
Has anyone identified the solution to this problem ?.

I am getting exactly the same error on a T23 thinkpad when trying to read a DVD (either of video or data) but it is still fine when reading CDs.

This used to work fine under Hoary but no longer seems to function under Breezy . I have even upgraded my version of pmount from the breezy-backports but that didn't help.

---

### Post by kpaull on 2005-12-29
I am too having similar pmount problems.  An ideas what to look for?

---

### Post by roach of discord on 2005-12-31
I'm having trouble with my upper cdrom drive.

This is what I get:

posthuman@ubuntu:~$ sudo mount -t auto /dev/hdc /mnt/cdrom
mount: No medium found

It seems that this is a common problem.  I am simply trying to mount a data CD.  This happens very often.

---

