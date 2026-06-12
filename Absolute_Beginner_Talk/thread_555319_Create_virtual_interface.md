---
title: "Create virtual interface"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by hannaman on 2007-09-20
I am trying to set up a virtual interface off of my primary eth0.
I would like to have eth0 use dhcp and eth0:1 use a static IP address.  I want to keep the dhcp so that network manager manages that port so I don't have to learn how connect to my company VPNs another way, but I want a static virtual interface so that I can use for my web server and not have to be concerned about changing port forwarding if the dhcp changes, etc.

Here is I what I have for /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet static
address 192.168.2.200
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
hardware address 00:11:11:C2:C8:03
```

I am not sure about the hardware address line.  I read on another forum that the MAC addresses should be different so I made slight changes to the actual MAC address.
Here is what happens when I restart networking:
```
 * Reconfiguring network interfaces...                                         
There is already a pid file /var/run/dhclient.eth0.pid with pid 14797
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:11:c1:c7:02
Sending on   LPF/eth0/00:11:11:c1:c7:02
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
SIOCDELRT: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:11:c1:c7:02
Sending on   LPF/eth0/00:11:11:c1:c7:02
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
SIOCADDRT: File exists
bound to 192.168.2.2 -- renewal in 488780 seconds.
SIOCSIFFLAGS: Cannot assign requested address                                   [ OK ]
```

I see that it cannot assign requested address, but I am unsure why.  If I static just eth0, that address gets assigned no problem, but Network Manager no longer manages the interface obviously.

Thanks

---

### Post by hannaman on 2007-09-21
For those that are concerned (since no one replied, I assume no one is) I finally resolved this issue.  Here is what my /etc/network/interfaces file looks like now:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
hwaddress ether 00:11:11:C1:C7:02

auto eth0:1
iface eth0:1 inet static
address 192.168.2.200
netmask 255.255.255.0
gateway 192.168.2.1
hwaddress ether 00:11:11:C1:C7:02

```

I can now access my website through the static virtual IP and still have network manager manage  eth0 and my VPN connections.

---

### Post by Yfrwlf on 2007-12-27
> **hannaman said:**
> For those that are concerned (since no one replied, I assume no one is) I finally resolved this issue.  Here is what my /etc/network/interfaces file looks like now:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
hwaddress ether 00:11:11:C1:C7:02

auto eth0:1
iface eth0:1 inet static
address 192.168.2.200
netmask 255.255.255.0
gateway 192.168.2.1
hwaddress ether 00:11:11:C1:C7:02

```

I can now access my website through the static virtual IP and still have network manager manage  eth0 and my VPN connections.

I know this is old and you probably don't care, but thanks for posting all this, I was wondering about setting up virtual interfaces for multiple websites off one apache server so this helped me, thank you!!

---

### Post by eode on 2008-03-21
I found this useful, too.  Thank you.  :-)

---

### Post by shimmyt on 2008-06-12
Still helpful :)

---

### Post by valeriupalos on 2008-07-05
Yup, still helped!

---

