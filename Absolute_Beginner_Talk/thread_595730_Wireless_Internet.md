---
title: "Wireless Internet"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by sarahdanielle on 2007-10-29
I just installed Ubuntu and inadvertently uninstalled Windows in the process. I am not familiar at all with this operating system, and I do not know how to get my wireless internet to work. The "Restricted Drivers" thing tells me that "The software source for bcm43xx-fwcutter is not enabled." How do I fix this?

---

### Post by MaximusTG on 2007-10-29
Assuming the computer you installed ubuntu on, also has cabled internet access (or you have the possibility to give it temporary internet access via a cable) , go to 

System (on the top panel) -> Administration -> Software Sources (enter your password) and check the box next to the line saying "Propietary drivers" (restricted).

Then go to the restrictive drivers manager, and you should be able to install the driver for your wireless card.

That is probably the easiest way to install a driver for your wireless card. 

The driver that the restricted drivers manager installs is an open-source driver, but is restricted since it needs the bcm43xxx firmware (which is propietary) to function.

As an alternative to the open source driver, there is also 'ndiswrapper' which takes the Windows driver, and "wraps" it to your Ubuntu operating system.

Let me know if the wireless card functions with the bcm43xxx driver, if it doesn't I can help you install ndiswrapper

---

### Post by octesian on 2007-10-29
After you open the restricted drivers manager and check the box enabling the driver it will ask for a location of firmware driver.  You can find it here [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")

just make sure your card is supported:

[http://bcm43xx.berlios.de/?go=devices]("http://bcm43xx.berlios.de/?go=devices")

---

