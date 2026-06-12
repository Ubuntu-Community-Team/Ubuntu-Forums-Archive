---
title: "Wireless down, I repeat Wireless....."
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-06-18
****hi
I have managed to connect my wirless lan cardbus EW-7108PCg IEEE 802.11g Edimax, but, as I will show, it does not seem to recognice the driver. Moreover, It found the network that I have set up, but can not connect to it.
[FONT="Times New Roman"]****[/FONT] Here are the tests I did:

@wow:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2632 (2.5 KiB)  TX bytes:2632 (2.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:94:B7:CA
          inet6 addr: fe80::20e:2eff:fe94:b7ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1071983 (1.0 MiB)  TX bytes:200 (200.0 b)
          Interrupt:9

@wow:~$ ping 192.168.0.1
connect: Network is unreachable
@wow:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:0e:2e:94:b7:ca
Sending on   LPF/ra0/00:0e:2e:94:b7:ca
Listening on LPF/eth0/00:a0:cc:c0:15:29
Sending on   LPF/eth0/00:a0:cc:c0:15:29
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15

Moreover when running the device manager it gives me that the vendor is RALink Device is unknown (0x0301) Bus type PCI

In network tools it confirms unknown interface (raO)
IPv6 fe80::20e and so on
I was thinking that maybe disabling IPv6 could do the trick.

Running wireless assistant it shows me the network but does not connect. When I run it it asks: "you might have insufficient  permission for wireless assistant to function properly"
"Did you run it using 'sudo'?" it asks, I organiced with synaptic. Should I run it in terminal?

Any help would be grately apreciated****

---

### Post by hajk on 2006-06-18
I'm not sure I understand everything you're saying in your post. Have you opened the System -> Administration -> Networking menu? If so, does it show a wireless interface? Then highlight it and configure its Properties before activating it.

---

