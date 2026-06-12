---
title: "ralink problem with /etc/init.d/networking or how to bugreport"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by GNUtoo on 2006-08-21
ralink card is ra0
/etc/init.d/networking check for:
```
# /etc/init.d/networking start
 * Configuring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```
but doesn't check for ra0 that is the ralink device
result:my card doesn't autoaticaly start like my atheros(ath0) does

what should i do?

this is important because it's for a person that doens't know anything about computer and so i won't tell the person to learn how to connect to internet with the graphical tools that are present in ubuntu(netwoking)

---

### Post by GNUtoo on 2006-08-21
i don't know the package name fo this script!!!
(for bugreporting)

---

### Post by hw-tph on 2006-08-21
First check if your /etc/network/interfaces file is OK. Do you really have eth1, eth1, wlan0 and ath0 devices in your system?

And you can user [packages.ubuntu..com](http://packages.ubuntu.com) to see what files belong to what packages. In this case it belongs to the netbase package.


Håkan

---

### Post by vbatts on 2006-12-10
first i would check /etc/network/interfaces to make sure that ra0 is configured in there. it should look something to the effect of

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp



iface ra0 inet dhcp
wireless-essid <ESSID>
wireless-key <WEP-KEY>

auto ra0

```

and for me i removed all the other interfaces because i don't have a need for them.

after that just 

```
sudo /etc/init.d/networking restart
```

---------------

as far as the deb that owns /etc/init.d/networking, it netbase.
 you can find that by typing

```
dpkg-query --search /etc/init.d/networking
```
and you'll see a little print
```
netbase: /etc/init.d/networking
```

---------------

if all else fails, learn how to use iwlist, iwconfig, and dhclient

vb

---

