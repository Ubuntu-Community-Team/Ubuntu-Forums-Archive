---
title: "Cant find usb printer!"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by zanazzi on 2007-07-13
I'm using kde!

I'm trying to get my epson stylus photo 895 working, and I'm struggling

its connected via usb but when i run the add printer prog from the control center it doesn't seem to be able to find it!

I have run lsusb in konsol with the following result;

```
me@me-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp.
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 005: ID 069a:0318 Askey Computer Corp.
Bus 004 Device 004: ID 0461:4d16 Primax Electronics, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 062a:0201 Creative Labs
Bus 001 Device 001: ID 0000:0000

```

the printer set-up thingy is asking for a url for the printer, i have no idea how to find this, plz help?

---

### Post by freesitebuilder on 2007-07-13
This page lists supported Epson printers [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersEpson](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersEpson)
but I can't see that one.  You could try adding it, as that seems to have worked for a user with photo 830 (system > admin>printing).

---

### Post by zanazzi on 2007-07-13
the problem i have is finding its location, there is adriver for the 870 in fiesty but the only way i know that is by selecting the option for parrallel printer, obv that deosn't work since its usb but i was thinking maybe i could edit the config after to change from serial to usb.

any ideas?

---

### Post by zanazzi on 2007-07-13
kk i found the problem

the usb hub that i was run through isn't reckognising is, if i plug it directly into the desktop lsusb  finds it

---

