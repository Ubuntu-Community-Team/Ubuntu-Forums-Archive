---
title: "unknown error-when eject button is pushed"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by rolypolycat on 2007-09-14
Hello!

I seem to have a problem  ejecting cd's or dvd's from my internal dvd-rw drive. Before, all I had to do was right-click on the drive icon, hit "eject volume", and it ejected the disk. Now, I'm getting this message when I click "eject volume": eject failed. cannot eject name of disk-unknown error. If I just hit the eject button, I get this message: failed to eject /org/freedesktop/HAL/devices/storage_model_DVDRW_LH_16W1p. Given device -long error message as above-is not a volume or a drive.
When I want to eject a disk, I have to click "unmount volume" first, then "eject volume. It does this for all users.  And for some dvd's, it won't eject at all, no matter what I do. I have to reboot to get that disk out of the drive.
I'm using Feisty Fawn, Xubuntu desktop.
This is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b5315d0d-21fc-44ec-89a6-31ef29ee8fa9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4ebdbd7d-bb8b-420d-b0fb-da0a8768c0a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Any help is greatly appreciated. Thanks!:confused:

---

### Post by splintercellguy on 2007-09-14
I actually have the same issue. I just call eject from command line.

---

