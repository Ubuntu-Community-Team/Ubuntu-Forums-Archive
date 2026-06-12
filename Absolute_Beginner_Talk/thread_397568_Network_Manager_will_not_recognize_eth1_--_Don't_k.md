---
title: "Network Manager will not recognize eth1 -- Don't know what I did !!"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-03-30
Well guess I messed something up really bad, but don't know when I did it. I had the network up and running just fine bout 2 weeks ago, with a network printer (HP C5140) being used by three comps (Compaq 5900z-Ubuntu 6.06.1, Toshiba Satellite Pro-dual boot XP and Dapper, and Gateway Media Center Edition-XP only). All three could ping each other and showed up on the network, and all could print flawlessly. I can't remember if I downloaded anything about two weeks ago or not (I know, I should write this stuff down and will in the future) but about that time the laptop and the Compaq could no longer print, though they could still ping each other just fine. The XP comp could and can still print no problems. When I restart Network Manager in terminal I get the following message
" * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:02:2d:86:00:49
Sending on   LPF/eth2/00:02:2d:86:00:49
Sending on   Socket/fallback
DHCPRELEASE on eth2 to 192.168.0.1 port 67
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

Listening on LPF/eth2/00:02:2d:86:00:49
Sending on   LPF/eth2/00:02:2d:86:00:49
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping."
Anyone have any idea what I did or maybe how to fix it ?? Will removing  and reinstalling Network Manager possibly fix the problem ? Looks like to me eth1 isn't there anymore. Your help is greatly appreciated by this desperate dude !!

---

### Post by zvacet on 2007-03-30
> disabling network manager in the sessions/startup bit, and typing 

sudo ifup eth0
sudo ifdown eth0
sudo ifup etho

replace eth0 with eth1 or whatever you use.I hope it helps.

---

