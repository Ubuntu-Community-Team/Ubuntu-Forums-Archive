---
title: "wifi problems rt2500"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-08-04
I am having trouble getting my rt2500 wifi card working with Ubuntu 7.04. I have read a half dozen howto's but it gets me nowhere. Finally I decided to disable the Networkmanager and see if I could bring the card up in with command lines. (Oh I tried Network-manager both with and without WEP) nothing seems to work. Somewhere in all the reading I did I found a command to see if the drivers were installed properly but I cannot find it now. Anyway, one time i was able to connect from the command lines but the next time I tried I got the following:
tim2@tim2-desktop:~$ sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 6392
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:11:09:07:f4:1f
Sending on   LPF/ra0/00:11:09:07:f4:1f
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.1.7
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.1.4
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


Any ideas how I can get this wireless card working.

Thank you, Tim

---

### Post by anewguy on 2007-08-04
You may want to check [[COLOR="Red"]this link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=515378") to see if it helps you.  Please post back if it does!:)

---

