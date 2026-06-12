---
title: "/dev/usb in fedora = what in ubuntu?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by fatdaddy on 2006-07-29
Challange,

I have a BELKIN UPS on a dual boot winxp :( and dapper :).

The belkin works fine in windows, however i want it to work in Ununtu.

During the installation it asks for the port, ie tty1, tty2 or usb (default = /dev/usb.  No such critter in ubuntu.  So what is the path to the usb ports that can talk to my UPS.  The ups shows up in kubuntu sysinfo and in lsusb
zack@zbuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 003: ID 050d:0910 Belkin Components
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
zack@zbuntu:~$
However i cannot find the proper way of inputting the path for the belkin.

Any and all help appreciated.

---

### Post by grizzly on 2006-07-29
Just guessing .. my pendirve is detected at /dev/sda1 .
so try "ls /dev/sd*"

---

