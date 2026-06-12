---
title: "Asus WL-167g"
date: 2008-12-04
forum: Apple Hardware Users
---

### Post by kozimodo on 2008-12-04
I just bought an Asus WL-167g for an old iMac G3 because I had read that it worked with Ubuntu but this does not appear to be the case for PPC.  I have xubuntu 8.04.1 installed but after plugging the usb dongle in and booting up, the rt73usb driver was not automatically loaded.  I modprobed it but there were still no wireless extensions.  I also tried adding it to /etc/modules and doing an update-initramfs.  Now when I boot, the module is loaded but still no wireless extensions.  Any ideas how to get the thing working?  Suggestions for other USB wireless cards that work with PPC?

From lsusb:
```
Bus 001 Device 004: ID 0b05:1723 ASUSTek Computer, Inc.
```

---

### Post by kozimodo on 2008-12-05
Solved.  I'm guessing that the problem was that the dongle was not getting enough power plugged into the keyboard.  Works fine plugged directly into the iMac.

---

