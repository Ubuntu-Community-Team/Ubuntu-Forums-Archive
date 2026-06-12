---
title: "newbie wireless troubleshooting"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by idioptilon on 2007-05-26
Hello all,

I have given this several days of work looking through the forums and wikis, and have made some progress, but have decided it is time to seek outside help.

Since nuking XP and reinstalling with Dapper two weeks ago, my first try with Linix, I have not been able to get a wireless connection, which is critical as I poach off the neighbors and don't have my own.  Everything fine with ethernet (using at a friends house).  On the WIFI troubleshooting page, I got as far as recognizing the router and have utterly failed.  The wireless card is recognized and the driver works, I also downloaded KWiFiManager which picks up the network (this took me a long time to figure out), but lists no access point.  Same thing in iwconfig (shows the access point as not associated).  It shows the connectivity as being excellent, but can't get the access point so that they recognize each other.

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STA8349BA"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=52/100  Signal level=34/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

If I am missing key info here let me know so I can post it.  Thanks a lot in advance.

---

### Post by AAM on 2007-05-26
there are some things that I can think of:

1. your "mate" down the road has wised up to his broadband loss and installed some encryption on his wireless
2. you need to associate properly - try the sudo ifup wlan0, sudo ifdown wlan0, also restart the dhcp client (dhclient)
3. be nice and go and find the owner of the wireless and offer to pay for your broadband usage - ??

---

### Post by idioptilon on 2007-05-27
Thanks for the reply:

1.  Nope, I can't get any network anywhere to connect
2.  On to something here printout from 

hosner@hosner-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:06:5b:d5:b4:a8
Sending on   LPF/eth0/00:06:5b:d5:b4:a8
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:13:10:83:49:ba
Sending on   LPF/wlan0/00:13:10:83:49:ba
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:06:5b:d5:b4:a8
Sending on   LPF/eth0/00:06:5b:d5:b4:a8
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 37185 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:13:10:83:49:ba
Sending on   LPF/wlan0/00:13:10:83:49:ba
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

So this certainly seems to be the problem, so how does one resolve it?

3.  The neighbor is cool with it.

---

