---
title: "connecting to wireless network"
date: 2008-03-29
forum: Apple Intel Users
---

### Post by jeremy.lynch on 2008-03-29
Hi,

I have a first generation macbook with atheros wifi card. I'm using kubuntu 7.10 and the install went smoothly. I need to connect to a "Bebox" wireless network. After installing wlanassistant i can see the network but it fails on trying to connect. The output is:
```
Loaded application options.
All interfaces: ath0, eth0, wifi0
Wireless interface(s): ath0
Permissions checked.
DHCP Client: dhclient
All executables found.
scan: /sbin/iwlist ath0 scan
Networks found: 10
ACTION: CONNECT.
Running DHCP client found.
kill_dhcp: /sbin/dhclient -r ath0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:41:8b:89
Sending on   LPF/ath0/00:17:f2:41:8b:89
Sending on   Socket/fallback
No pre-connection command specified.
iwconfig_set: /sbin/iwconfig ath0 mode managed channel 6 key off essid BeBox
iwconfig_ap: /sbin/iwconfig ath0 ap 00:90:D0:F4:2D:55
ifconfig_dhcp: /sbin/dhclient ath0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:41:8b:89
Sending on   LPF/ath0/00:17:f2:41:8b:89
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
Running DHCP client found.
kill_dhcp: /sbin/dhclient -r ath0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:41:8b:89
Sending on   LPF/ath0/00:17:f2:41:8b:89
Sending on   Socket/fallback
CONNECTION FAILED.
disconnect: /sbin/iwconfig ath0 mode managed key off ap off essid off
Application options saved.
Kernel socket closed.

```

Many thanks for any help you can offer.

Jeremy.

---

