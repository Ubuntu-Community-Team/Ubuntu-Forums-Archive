---
title: "xorg.conf setup - 2 monitors - 2 pci cards"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by nickburns on 2006-10-23
I am frustrated as can be with my setup.  I have identical two PCI cards, in slots 1 and 2 (0:8:0 - 0:9:0) and two identical dell M991 monitors.  I have not been able to get my setup to work with both monitors.  I have found and read hundreds of threads on setting up the xorg.conf file, but with no luck.  

Both cards require the vesa driver, not the fancy ati / nvidia stuff.  I love ubuntu and don't want to give up on it.  Both cards light up, and the monitors show crazy color lines, but the system freezes up every time.

Please someone help...

---

### Post by CatKiller on 2006-10-23
I'm not sure that it'll make that much difference to you, since you're experiencing a crash that probably isn't to do with the monitor settings, but [Dell claim]("http://support.dell.com/support/edocs/monitors/49vyr/en/spec/spec.htm") that the Horizontal Scan range is 30-96kHz. It should display **something** though, even with a lower range, surely.

Also, there is a "cirrus" driver that might help. It's disturbing that the VESA driver doesn't work for you though.

---

