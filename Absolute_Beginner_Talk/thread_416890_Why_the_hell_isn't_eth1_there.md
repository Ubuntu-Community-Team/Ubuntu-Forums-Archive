---
title: "Why the hell isn't eth1 there"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-04-21
Someone please tell me why the hell my eth1 keeps suddenly disappearing. I update to Feisty, and it's there. I try to install the drivers for it and the damned thing suddenly just disappears. I don't get it. Why the hell is this being such a problem?

In the terminal when I try to connect:
```
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

When I try to do it graphically, none of my Wifi detection programs are picking up my wireless router, and when I go to the Network Settings the only thing there is eth0. I'm getting really really pissed off.

---

### Post by bloodniece on 2007-04-21
I suspect it has need renamed.  After updating to Feisty my eth1 was renamed to ath1.

maybe take a look at /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
or 
sudo kate /etc/network/interfaces
```

---

### Post by Baelfael on 2007-04-21
I figured it out... typing in "sudo modprobe bcm43xx" added it back on again.

---

