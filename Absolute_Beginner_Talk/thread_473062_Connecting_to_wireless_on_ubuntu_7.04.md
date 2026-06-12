---
title: "Connecting to wireless on ubuntu 7.04"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Dman87 on 2007-06-13
I have a belkin wireless G pluss MIMO router and cant connect to my wireless desktop(windows xp). I want to connect from laptop with ubuntu live cd. I want to see it the ndiswrapper thing would work but when i search for the packages in the synaptic package manager it only finds common and -utils. 
Also when i put the wired cable in the back of the laptop to download the packages i could not get the net on it eather it siad it was connected but i couldent get the browser to get a web page up.

**sudo lshw**
*-network DISABLED
description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@03:03.0
logical name: eth1
version: 03
serial: 00:0b:7d:17:d8:9e
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
resources: iomemory:dfcfe000-dfcfffff irq:18

[B]
sudo ifconfig -a[/B]
eth0 Link encap:Ethernet HWaddr 00:11:43:4B:8C:75
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16

eth1 Link encap:Ethernet HWaddr 00:0B:7D:178:9E
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 Base address:0x4000

eth0:avah Link encap:Ethernet HWaddr 00:11:43:4B:8C:75
inet addr:169.254.5.242 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:36 errors:0 dropped:0 overruns:0 frame:0
TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2664 (2.6 KiB) TX bytes:2664 (2.6 KiB)


**sudo iwconfig**
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"" Nickname:"Broadcom 4306"
Mode:Managed Access Point: Invalid
RTS thrff Fragment thrff
Encryption keyff
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


**sudo ifdown eth0**
ifdown: interface eth0 not configured

[B]
sudo killall dhclient[/B]
dhclient: no process killed


**sudo iwconfig eth1 essid Donaldson mode managed enc off**
no reslut, must have done the command.

[B]
sudo dhclient -d eth1[/B]
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:0b:7d:17:d8:9e
Sending on LPF/eth1/00:0b:7d:17:d8:9e
Sending on Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

any thoughts?

---

### Post by Mazza558 on 2007-06-13
You need to actually install Ubuntu to get the BCM drivers working, in general. 

Download the file attached, put it on a flash drive and when you've installed Ubuntu run that file. It will ask if you want to install it, as well as your password. Install, then just reboot and you should be good to go.

---

### Post by Dman87 on 2007-06-13
WOWOW great u got it in 1 :P, works fine on live cd, also works with that WPA no probs. where did u find that, how did u know it would work ...... tis great. 

ps do you know if theres somthing out there that would make knoppix work as well? still a bit new to linux trying the live cds out first.

---

