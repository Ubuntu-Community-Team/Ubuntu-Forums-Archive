---
title: "How do I mount a USB hard drive?"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by yanewby on 2006-10-25
I have just purchased a USB hard drive enclosure and stuck an old hard disk I had lying around in it in the hope I could use it as some removeable storage.

The instructions that cam with the enclosure were vague and I have given them below:

1) Execute cd /etc/sysconfig/ (cat /etc/sysconfig/hwconfig | more)
2) Check the device information in hwconfig write down the mount point.
3) Make a directory in /mnt (ex: mkdir /mnt/usbHD)
4) Then, execute mount /dev/sda1 /mnt/usbHD (if mount point was .dev/sda)

From what I understand of these instructions I am meant to use hwconfig to discover the "mount point" of my usb enclosure.  How do I do this?

How do I then use this information so that each time I plug in my enclosure it appears on my desktop?

I have looked around the forum and there appear to be a few other threads with similar problems and I have tried to follow them but I am stuck at point 1 above still.

Any help in this will be gratefully accepted!

(If it helps I am running Dapper Drake.)

---

### Post by ReaderRat on 2006-10-25
[HOWTO Write To EXT. USB HDD](http://www.ubuntuforums.org/showthread.php?t=276272)

---

### Post by yanewby on 2006-10-25
Thanks for the response ReaderRat but this does not help me.

I am pretty sure the drive is formatted with FAT32 but it *could* be NTFS.  I would like instructions on how to understand the instructions I have been given with the enclosure, for example a solution to how I discover the "mount point" of my usb enclosure and how to set the enclosure up so that each time it is plugged in it appears on my desktop.

---

