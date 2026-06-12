---
title: "Ndiswrapper + MacBook Pro + Feisty: wlan0 error"
date: 2007-05-05
forum: Apple Intel Users
---

### Post by ExplodingPickle.org on 2007-05-05
I've tried getting wireless on my Airport Extreme with madwifi or bcm43xx already, but neither worked. Now with ndiswrapper I get this error when I try restarting the network (/etc/init.d/networking restart) or ifup wlan0:

```
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
```

I seem to get the same errors for eth1, ath0, and ath1. The only interfaces that show up are eth0 an lo.

---

