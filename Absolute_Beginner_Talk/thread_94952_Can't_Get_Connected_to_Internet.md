---
title: "Can't Get Connected to Internet"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by Oracle of Wuffing on 2005-11-25
I use a Cable Internet connection at home with an ethernet cable connecting a computer to a modem directly (in other words, no router), obtaining an IP via DHCP.  The modem is a Motorola Surfboard, and normally I can just pass the ethernet cable to another computer when one needs internet access.  I've tried enabling, disabling, and re-enabling the onboard port through the Networking Administration, as well as rebooting and unplugging the modem in between.

When the modem is connected to the Ubuntu machine, I get a blink of PC Activity every two and a half seconds.

Here's what I'm getting for ifconfig, don't know it it helps:
eth0
Link encap:Ethernet HWaddr 00:11:D8:D5:7C:67
inet6 addr: fe80::211:d8ff:fed5:7c67/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueulen:1000
RXbytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:17

---

### Post by Ruso on 2005-11-25
Is your network connection set do use DHCP for eth0?? Because as I see you dont have any IP address.

---

### Post by Oracle of Wuffing on 2005-11-25
Yes, eth0 is configured to use DHCP.

---

### Post by cwaldbieser on 2005-11-25
[QUOTE=Oracle of Wuffing]Yes, eth0 is configured to use DHCP.[/QUOTE]
Open a terminal and try:
```

$ sudo dhclient eth0

```
That should make your ethernet card request an IP address from your ISP's DHCP server.  Then ifconfig should show you an IP address.

If the command spits out errors, post them back.

---

### Post by Oracle of Wuffing on 2005-11-25
Here's what I got from dhclient:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:11:d8:d5:7c:67
Sending on   LPF/eth0/00:11:d8:d5:7c:67
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by cwaldbieser on 2005-11-26
[QUOTE=Oracle of Wuffing]Here's what I got from dhclient:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:11:d8:d5:7c:67
Sending on   LPF/eth0/00:11:d8:d5:7c:67
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/QUOTE]

Hmm, what is supposed to happen is you should get something like:
```

DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.2 -- renewal in 122624 seconds.

```
At the end.  Of course, this example uses IP addresses from a local network.  You should get the offer from your ISP's DHCP server.

Do you have another OS you can connect with?  For example, can you connect with a Knoppix Live CD?  If you have another GNU/Linux PC that can connect, you could just examine the DHCP settings and see if something needs to be changed in your Ubuntu setup.  The config is /etc/dhcp3/dhclient.conf.  You might just need to tweak some settings to have a longer timeout, for example.

---

