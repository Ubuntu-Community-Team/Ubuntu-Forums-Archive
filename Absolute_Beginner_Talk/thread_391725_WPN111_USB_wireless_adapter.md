---
title: "WPN111 USB wireless adapter"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-03-23
I am having trouble getting my Netgear WPN111 USB wireless adapter to work.

I think I have installed the driver but I'm not sure. When I type ndiswrapper -1 I get the following result but i don't really understand what it is telling me.

david@david-desktop:~$ ndiswrapper -1
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
david@david-desktop:~$ 

Can someone help please?

---

### Post by compmodder26 on 2007-03-23
That "-1" should be a lowercase L.  Try that, then post the output you receive.

---

### Post by OldDog11 on 2007-03-23
The output is:

david@david-desktop:~$ ndiswrapper -l
Installed drivers:
netwpn11        invalid driver!
david@david-desktop:~$

---

