---
title: "No working leases in persistent database - sleeping."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-02-24
when i try to connect to the internet using my wireless card i get this error

coubury@coubury-desktop:~$ rutilt
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSListening on LPF/wlan4/00:0e:2e:c8:4e:08
Sending on   LPF/wlan4/00:0e:2e:c8:4e:08
Sending on   Socket/fallback
DHCPDISCOVER on wlan4 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan4 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan4 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan4 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

it shows im connected! in my wireless utility

[http://img406.imageshack.us/img406/7127/screenshotxj6.png](http://img406.imageshack.us/img406/7127/screenshotxj6.png)

[http://img245.imageshack.us/img245/7509/screenshot1co4.png](http://img245.imageshack.us/img245/7509/screenshot1co4.png)

---

### Post by paultag on 2008-02-24
you are failing to join the network, as well as receive DHCP offers. 
what are the outputs of these commands?

```

iwconfig
iwlist
iwlist <ETH_DEVICE> scan

```

(Where <ETH_DEVICE> is your wireless device name, usually eth0 or eth1.)

::EDIT::
looks like the <ETH_DEVICE> is wifi4 or wlan4

---

### Post by asmoore82 on 2008-02-24
I used to get this error a lot on 7.04 Fiesty, but since the change to 7.10 Gutsy, everything is perfect.
turning all networking completely off and on again helped, as did switching network profiles,
even it it was re-loading the same profile, and turning wired ethernet off.

---

### Post by paultag on 2008-02-24
also, have you tried nm-applet? its pretty good.

---

