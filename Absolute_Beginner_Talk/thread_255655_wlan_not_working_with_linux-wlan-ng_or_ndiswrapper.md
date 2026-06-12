---
title: "wlan not working with linux-wlan-ng or ndiswrapper"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by nitewing98 on 2006-09-11
I'm very frustrated and disheartened.  I've tried for 3 days to get my NIC up.  It's a Netgear MA111, v2.  I've tried the linux-wlan-ng driver, the ndiswrapper with both the Netgear driver and the SIS driver from [www.sis.com](www.sis.com).  Nothing so far has worked.

After installing the linux-wlan-ng mod, I got this:
$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

So I tried ndiswrapper, and when I use the command "ndiswrapper -l" it tells me "driver present", but not "hardware present."

Has anyone been able to get this working?

---

### Post by tormod on 2006-09-27
FYI, the v2 does not use linux-wlan-ng. See [https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111")

---

