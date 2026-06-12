---
title: "ubuntu bridge"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by falcons7 on 2007-02-11
hello I am trying to set up a network bridge from my pc(wireless eth1, wired eth0). to connect my Ps2 via crossover cable... i have the bridge setup although when I connect to the net with my PS2 i can gain a connection to the wired network and My wireless is dropped... i can paste my /etc/network/interfaces.... I am on edgy and am using gnome network manager

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface br0 inet static
bridge_ports eth0 eth1
address 192.168.1.109
netmask 255.255.255.0

here is when i restart my network service

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6877
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:a0:d1:48:32:c6
Sending on   LPF/eth0/00:a0:d1:48:32:c6
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.254.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 6910
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:a7:a5:7f
Sending on   LPF/eth1/00:13:02:a7:a5:7f
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:a0:d1:48:32:c6
Sending on   LPF/eth0/00:a0:d1:48:32:c6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:a7:a5:7f
Sending on   LPF/eth1/00:13:02:a7:a5:7f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 36167 seconds.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


*note i have also tried using dhcp..... any help?

---

### Post by falcons7 on 2007-02-12
bump

---

