---
title: "Broadcom BCM4310 help needed"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Valehru on 2006-11-22
Heya.

I have the following wifi card in my Compaq v3000 laptop:

> 0000:01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)


I'm running Dapper Drake on an x32 system.  Right now through network-manager I cannot see my wireless card, there is not an eth1 card available.

> valehru@valehru-laptop:~$ sudo ifup eth1
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.


I feel like I'm banging my head off of a wall.  Any help would be really appreciated. ](*,)

---

### Post by Sgood1971 on 2006-11-22
[This thread]("http://ubuntuforums.org/showthread.php?t=185174") did the trick for me.

---

### Post by crimesaucer on 2006-11-22
That above thread worked for me too, but I had to also install "wifi-radar" to easily detect a wifi signal since my xubuntu network manager was confusing. This is the wifi-radar link: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

---

