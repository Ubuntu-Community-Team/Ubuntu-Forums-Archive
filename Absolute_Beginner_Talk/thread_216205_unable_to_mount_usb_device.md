---
title: "unable to mount usb device"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by harys on 2006-07-15
hi, i've done a wrong configuration of may graphic card ati and yet when i boot up X window don't start.
i booted from the cd live dapper and all went on normally so i copied the xorg.conf to the usb device. then i booted from the harddisk wasn't able to mount it from tty1 so that i could copy the xorg.conf in /etc/x11/.i tried mount /dev/sda but it didn't work. 
i mounted the dapper from cd drive and issue the ls command but didn't know where to find the xorg.conf file.

thanks for your help.
harys

---

### Post by [S|G] on 2006-07-15
You can probably find xorg.conf in /etc/X11 (case sensitive). As for your usb drive, try mounting /dev/sda1 instead of /dev/sda

---

