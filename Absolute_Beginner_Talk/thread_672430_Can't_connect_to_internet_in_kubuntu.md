---
title: "Can't connect to internet in kubuntu"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Ludford on 2008-01-19
I can't connect to the internet in kubuntu. I have a connection where my computer plugs straight into my broadband modem via ethernet cable.

So what settings do I need to use in the configuration screen?

What TCP/IP address... Dhcp or Bootp My Ip says that it is 169.254.8.104 but what netmask?

what do I put in for my default gateway IP and what DNS Ips do I need to put in.

My interface is called eth0 and is enabled.

I know nothing about any of this because when I boot into XP it does it all automatically.

Thanks for any help.

---

### Post by Ludford on 2008-01-19
I ran ipconfig in windows cmd and I got Ips for submask and gateway so I guess I should just put these in right?

EDIT. My netmask is 255.255.252.0 but that isn't available in the drop down list

---

### Post by Ludford on 2008-01-19
No it;s still not working :(

---

### Post by Ludford on 2008-01-19
ifconfig outputs:

```
Link encap:Ethernet  HWaddr 00:11:D8:C6:A2:5C
          inet6 addr: fe80::211:d8ff:fec6:a25c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xcc00

eth0:avah Link encap:Ethernet  HWaddr 00:11:D8:C6:A2:5C
          inet addr:169.254.8.104  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4864 (4.7 KiB)  TX bytes:4864 (4.7 KiB)
```

route, outputs:

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0


sudo /etc/init.d/networking restart, outputs

```
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6091
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:d8:c6:a2:5c
Sending on   LPF/eth0/00:11:d8:c6:a2:5c
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:d8:c6:a2:5c
Sending on   LPF/eth0/00:11:d8:c6:a2:5c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


Can anyone see the problem?

---

