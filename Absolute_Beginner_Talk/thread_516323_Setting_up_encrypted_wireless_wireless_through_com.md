---
title: "Setting up encrypted wireless wireless through command line"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Venerence on 2007-08-03
Whoops, put wireless twice in the title.

Unfortunately, the computer I'm installing ubuntu on has a radeon x1700, and as such I'm experiencing the bug described here: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194).

To fix that (and get to the graphical page), I need to get my internet connected to a WPA encrypted wireless router through command line.

currently my /etc/network/interfaces file displays the following:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```
which doesn't tell me much. A scan (through iwlist scanning) shows the nearby wireless routers correctly, so I'm assuming my wireless drivers are working properly. Unfortunately, I don't know how to connect to the router itself from here (let alone a wpa encrypted one), and could use some help.

EDIT: the hardware detection shows that my wireless card is the following:
```
Product: PRO/Wireless 3945ABG Network Connection
Vendor: Intel Corporation
Physical id: 0
bus info: pci@03:00.0
logical name: eth1
version: 02

```

---

### Post by Chris S. on 2007-08-03
You can use wpa_supplicant to connect to WPA protected access points (well, and just about anything else too).  I can't help with setting up WPA, never done it before.  But, there are some examples in /usr/share/doc/wpasupplicant, if that directory exists on your machine.  If those aren't there, then "man wpa_supplicant", forum search, or Google.

Hope it works for you.

---

