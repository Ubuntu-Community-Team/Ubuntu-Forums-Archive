---
title: "belkin F5D6020 wireless card does not work"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by phasenew on 2007-03-27
I just installed the Ubuntu 7.0.4 onto my sony vaio frv laptop. everything seems work fine except the Belkin F5D6020 wireless card (not version 2 or 3, just the very first version). I followed the instructions at [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux) to use the wrapper technique. after installed the driver, i did "sudo ndiswrapper -l", it shows that both the driver and hardware present.
but when i did "sudo ifup wlan0", an error message: 

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

Can anyone shed any light on this?
Thanks.

---

