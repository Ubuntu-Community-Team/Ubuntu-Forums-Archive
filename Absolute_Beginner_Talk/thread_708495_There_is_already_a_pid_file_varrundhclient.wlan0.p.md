---
title: "There is already a pid file /var/run/dhclient.wlan0.pid"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by PGScooter on 2008-02-26
Hi, I cannot connect to the internet, and was wondering if the following line is an error which would cause this problem:
"There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120"

or is that normal?

It is from the output below


roddick@Happy:/media/KINGSTON$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:e0:98:c6:48:ca
Sending on LPF/wlan0/00:e0:98:c6:48:ca
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.




just in case:
iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11b+/g+ ESSID:"2WIRE698" Nickname:"acx v0.3.36"
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
Bit Rate:1 Mb/s Tx-Power=15 dBm Sensitivity=1/3
Retry min limit:7 RTS thrff
Encryption key:3437-0574-81 Security modepen
Power Managementff
Link Quality=49/100 Signal level=29/100 Noise level=0/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by jw5801 on 2008-02-27
The PID line just tells you that dhclient is already running. Have you had a look at [this post](http://ubuntuforums.org/showthread.php?t=571188)? It might be worth a check, at the very least Kevdog might have a better idea about any issues if you posted the problem there. There've been quite alot of posts through the thread as well, so there should be some debugging options you can try.

---

### Post by PGScooter on 2008-02-29
Thanks jw5801! That thread was very useful (no I had not found it before)
You were right, it was the debugging on the replies that was the most helpful. dmesg turned up some interesting errors. I posted them so hopefully I'll get some feedback.

Thanks for the help!

---

