---
title: "MacMini lirc setup"
date: 2007-12-20
forum: Apple Intel Users
---

### Post by andry.korolyuk on 2007-12-20
Did anybody manage to setup lirc on latest macmini (Core 2 Duo)? It looks like appleir is in the kernel but chain is broken somewhere. apple remote buttons are binded to keyboard shortcuts in keyboard shortcut setup which makes me think that event information is received somehow. irrecord is failing with segmentation fault when button pressed. irw is not receiving anything. 

in /etc/lirc/hardware.conf
DRIVER="macmini"
DEVICE="/dev/input/event3"

---

### Post by solmis on 2007-12-23
Works fine here. Device may change on boot, so I'm using /dev/input/by-path/pci-0000:00:1d.3-usb-0:2:1.0-event- as the device for Lirc. Using macmini driver segfaulted irrecord here too,  but dev/input driver works fine.

Anyone know how to make it recognize other remotes? So far it only recognizes the Apple remote. I've tried several others with Logitech Harmony remote.

---

### Post by btucker on 2007-12-23
> **andry.korolyuk said:**
> Did anybody manage to setup lirc on latest macmini (Core 2 Duo)? It looks like appleir is in the kernel but chain is broken somewhere. apple remote buttons are binded to keyboard shortcuts in keyboard shortcut setup which makes me think that event information is received somehow. irrecord is failing with segmentation fault when button pressed. irw is not receiving anything. 

in /etc/lirc/hardware.conf
DRIVER="macmini"
DEVICE="/dev/input/event3"

I had the a similar problem. Too tired to be completely accurate...

In the kernel /dev/hiddev0 doesn't get created.  It's assigned to broken devices or some such gumf; Once I undid that it and recomplilled the kernel + the latest version of lirc it all worked.  

I'm sure a 'local' posted about it and even pestered the kernel developers.


Is the hardware capable of receiving from other remotes, that would be cool?

---

