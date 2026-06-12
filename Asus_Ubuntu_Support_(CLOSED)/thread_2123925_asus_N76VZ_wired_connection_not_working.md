---
title: "asus N76VZ wired connection not working"
date: 2013-03-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by himerus on 2013-03-09
hi,
I have recently purchased an Asus notebook N76VZ and installed Ubuntu 12.10.
The wired connection was not managed by NetworkManager I did an apt-get upgrade, and all the updates. After a restart my wired connection was finally managed by NetworkManager but still not working. 
The cable and the router works because my other laptop (Dell) that has a working internet connection; this one does not. The wireless connection works perfectly.

Can you please help me get my wired connection working ?

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 50:46:5d:e4:c7:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77397 (77.3 KB)  TX bytes:77397 (77.3 KB)

wlan0     Link encap:Ethernet  HWaddr 84:a6:c8:6a:6a:35  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a02:2f0a:3010:36b:86a6:c8ff:fe6a:6a35/64 Scope:Global
          inet6 addr: fe80::86a6:c8ff:fe6a:6a35/64 Scope:Link
          inet6 addr: 2a02:2f0a:3010:36b:e913:b51e:6639:fcd0/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9538720 (9.5 MB)  TX bytes:1157381 (1.1 MB)


[B]ethtool eth0
[/B]Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: Symmetric
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000060e4 (24804)
			       link ifup rx_err tx_err hw wol
	[COLOR="#FF0000"]Link detected: no[/COLOR]

**cat /etc/network/interfaces** 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


[B]cat /etc/NetworkManager/NetworkManager.conf 
[/B][main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=50:46:5D:E4:C7:C6,

[ifupdown]
managed=true


[B]dhclient -v -4 eth0
[/B]Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/50:46:5d:e4:c7:c6
Sending on   LPF/eth0/50:46:5d:e4:c7:c6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
..................................


ethtool says that there is no link detected but the cable works perfectly well for my other laptop , and also with this one, Asus, the router's greed led of the port is on, so there is power on the wire.   
please help me.

thanks a lot,
Viorel

---

