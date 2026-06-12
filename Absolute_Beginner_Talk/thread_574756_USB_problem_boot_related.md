---
title: "USB problem boot related"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by 1danjack on 2007-10-13
My pc has a usb mouse (always connected) working fine.

My two usb drives, ipod and windows formatted music data usb hard drive are not working fine.

if i boot my pc with no other usb devices attached they won't autorun.

Can i navigate to the drive though terminal?


If i boot my pc with any one of my usb drives attached all can be attached/ ejected again and again error free until next reboot.

Is there something I need to enable in /boot/grub/menu.lst ?

---

### Post by Pumalite on 2007-10-13
Check in /media and see if they are mounted. In reality they should automount.(or hot mount)

---

### Post by Pumalite on 2007-10-13
Check in Terminal:
mount

---

### Post by 1danjack on 2007-10-13
Hi thanks for quick in put.

I've ran as suggested please see copy of text from terminal:

```
dan@black-silver:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
dan@black-silver:~$ cd /media
dan@black-silver:/media$ ls -a
.  ..  cdrom  cdrom0  floppy  floppy0  .hal-mtab  .hal-mtab-lock
dan@black-silver:/media$ 
```

---

### Post by 1danjack on 2007-10-14
There is something strange afoot.
When I turned on this morning (without any USB drives attached) I stuck in my USB stick and automount success.

However I have since turned my machine off (withouth any USB drive attached) and now automount failure!

---

### Post by 1danjack on 2007-10-15
Today USB automount failure, let's see what tomorrow brings...

---

