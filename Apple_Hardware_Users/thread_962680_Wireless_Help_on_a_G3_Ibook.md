---
title: "Wireless Help on a G3 Ibook"
date: 2008-10-29
forum: Apple Hardware Users
---

### Post by gbrown1976 on 2008-10-29
Hello! I am a new user to Linux in general, and I just loaded Ubuntu 8.04 onto a 700 MHz PowerPC G3 Ibook
(640 MB SDRAM), and everything seems to have gone well so far. I am getting ready to try to install a RokAir wireless USB adapter (Realtek chipset), but I am not really sure how to proceed? I think I have the driver, but how do I load it? Thanks in advance!

Greg

---

### Post by ajmctaggart on 2008-10-29
Realtek does make some opensource drivers, but if you mean to use the XP/Vista Driver on this machine, that unfortunately will not work.  To my knowledge, ndiswrapper only works on i386, no PowerPC love...

If you have the Realtek Opensource driver, it shouldn't be too hard.

Here is a somewhat corresponding thread 
[http://ubuntuforums.org/showthread.php?t=177850]("http://ubuntuforums.org/showthread.php?t=177850")

Posting the output of ```
lsusb
``` in the terminal would help too, let you know what model your usb dongle "really," is...

madwifi may be a possiblility...don't know if they work w/ your model...
[madwifi.org](madwifi.org)

Good Luck!
ajm

---

### Post by DRM_free on 2008-10-30
Simply plugging the USB key while the computer is off in and then rebooting should work. If not, give 8.10 a try.

---

### Post by Jwav3 on 2008-10-30
> **DRM_free said:**
> If not, give 8.10 a try.

Be careful before you do that. 8.10 does not work on my system and it is very similar to yours. (you have a 700, I have a 900)

[http://ubuntuforums.org/showthread.php?t=961107](http://ubuntuforums.org/showthread.php?t=961107)

---

