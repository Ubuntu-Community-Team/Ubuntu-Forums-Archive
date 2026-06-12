---
title: "Internet Connection"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by theodore_kh on 2006-10-23
As usual, another newbie who face some common problems.

I just got myself the ubuntu 6.06. 

This is my first time, however I had quickly encounted an error which I couldn't figure it out. 


I can surf the net with firefox, yet I can't do any update or whenever my system needs to download stuff from the internet.

I'm using a proxy connection behind my university

This is my university  setup for internet connection on pc
[http://www.ntu.edu.sg/CITS/Getting+Help/ge...er+settings.htm](http://www.ntu.edu.sg/CITS/Getting+Help/get+me+connected/web+browser+settings.htm)

Below are some commands of my pc:
> ipconfig
[spoiler]eth1      Link encap:Ethernet  HWaddr 00:11:09:C4:EC:DB
          inet addr:172.20.66.29  Bcast:172.20.67.255  Mask:255.255.252.0
          inet6 addr: fe80::211:9ff:fec4:ecdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8096306 (7.7 MiB)  TX bytes:1201472 (1.1 MiB)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:872 (872.0 b)  TX bytes:872 (872.0 b)
[/spoiler]

> iwconfig
[spoiler]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.
[/spoiler]

> iwlist scan
[spoiler]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
[/spoiler]

> sudo /etc/init.d/networking restart
[spoiler] Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:11:09:c4:ec:db
Sending on   LPF/eth1/00:11:09:c4:ec:db
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 155.69.7.3 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:11:09:c4:ec:db
Sending on   LPF/eth1/00:11:09:c4:ec:db
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 172.20.67.252
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 172.20.67.252
bound to 172.20.66.29 -- renewal in 36615 seconds.[/spoiler]

> route
[spoiler]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.20.64.0     *               255.255.252.0   U     0      0        0 eth1
default         172.20.67.254   0.0.0.0         UG    0      0        0 eth1
[/spoiler]

> sudo gedit /etc/network/interfaces
[spoiler](gedit:6885): Gdk-WARNING **: locale not supported by Xlib

(gedit:6885): Gdk-WARNING **: cannot set locale modifiers
[/spoiler]

> sudo lspci
[spoiler]0000:00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
0000:00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
0000:00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
0000:02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
[/spoiler]

---

### Post by theodore_kh on 2006-10-23
Or can someone teach me how to configure my internet proxy connection?

**At the system > preferences> network proxy**
That one I choose auto configure with [http://www.ntu.edu.sg/proxy.pac](http://www.ntu.edu.sg/proxy.pac)

What is that one anyway? Even if I choose direct connection or manual or even type the address wrongly in auto configuration, it doesn't affect my surfing internet and MSN. Seems like it doesn't function anyhow.


and at the other at network settings under administration > network

I choose DHCP, or whatever is it , only that my internet will work. If I choose static I totally can't connect to my university website at all.

Inside the DNS it is auto configured for me
ntu.edu.sg
and the ip is 155.69.X.X. 


I already tried sudo apt-get update. But ubuntu can't detect the internet and cant update

---

