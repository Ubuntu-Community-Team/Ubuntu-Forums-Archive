---
title: "command"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by cjhardie on 2007-04-18
I need to know the command for finding computer information, such as Video Card.

---

### Post by wmcbrine on 2007-04-18
From the menu: Preferences, Hardware Information.

From the command line: It depends exactly what you want... there are a number of ways to get info. lspci, for example.

---

### Post by cjhardie on 2007-04-18
There is no hardware information in preferences,  and lspci isn't what I want.  I want to know what video card is in my computer

---

### Post by zvacet on 2007-04-19
```
lshw
```

---

### Post by wmcbrine on 2007-04-19
> **cjhardie said:**
> There is no hardware information in preferences, To clarify, I should've said *System*, Preferences, Hardware Information. Are you sure it's not there? The video card doesn't exactly stand out in the list, though.

lspci does show the video card, on my system. It looks like this (last line of the output):

01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 05)

Or look in /etc/X11/xorg.conf.

I know there used to be a more direct way to get this info, but I can't find it now.

---

### Post by compiledkernel on 2007-04-19
lsusb - for usb devices 

lspci - for pci devices 

cat /proc/meminfo - for memory

cat /proc/cpuinfo - for processor 

from the command line of course.

---

