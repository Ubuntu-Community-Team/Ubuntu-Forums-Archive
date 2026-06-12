---
title: "Mounting a second ext3 partition"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by halcyon on 2006-09-13
I have another ext3 partition in addition to my root partition that I use for storing data.  However, I can't find a way to make this partition automatically mount on boot, with read and write permissions for the default user created during Ubuntu's setup.  I can read the partition under my normal login, but only root is able to write to it.

I've tried various combinations of mount options in fstab, but haven't been successful thus far.

Here's my fstab (I set the option back to defaults after I got tired of fiddling):

[PHP]
# /etc/fstab: static file system information.
#
#DEV       POINT           TYPE         OPTIONS                     D  P
proc       /proc           proc         defaults                    0  0
/dev/sda7  none            swap         sw                          0  0
/dev/sda6  /               ext3         defaults,errors=remount-ro  0  1
/dev/sda8  /media/data     ext3         defaults                    0  0
/dev/sda1  /media/windows  ntfs         nls=utf8,umask=0222         0  0
/dev/hda   /media/cdrom0   udf,iso9660  user,noauto                 0  0
[/PHP]

andddd here's mtab:

[PHP]
/dev/sda6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
/dev/sda8 /media/data ext3 rw 0 0
/dev/sda1 /media/windows ntfs rw,nls=utf8,umask=0222 0 0
[/PHP]

Any help with this would be appreciated, I'm sure there's a way to do it somehow.

---

### Post by Kobalt on 2006-09-13
Hello,

Since it's ext3 format, have you tried configuring what you want from this menu : System->Administration->Disks ?

Cheerio !

---

### Post by djsroknrol on 2006-09-13
Try this in your fstab line...

         "**auto,rw,**    defaults"                    


That should give you automounting and read - write permissions.

---

### Post by halcyon on 2006-09-13
Kobalt, the program you mentioned offers nothing more than mount/unmount function and choose path to mount to, so no help there, but thanks anyways!

And for djsroknrol, auto and rw are included in the defaults option, but I tried it anyways on the hope it might work. Sadly, it didn't (I've tried just auto and rw by themselves too, no luck) :p

---

### Post by halcyon on 2006-09-13
! SHAMELESS BUMP !

It can't be that hard can it?

---

