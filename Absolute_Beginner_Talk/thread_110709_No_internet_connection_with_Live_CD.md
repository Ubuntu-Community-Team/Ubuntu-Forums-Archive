---
title: "No internet connection with Live CD"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by 30otsix on 2005-12-31
I just got this new computer and downloaded several live cds to test out some new distros and check out the hardware detection. I had been using Debian Sarge on older hardware without any issues, but since I had no issues, I know nothing about troubleshooting Ethernet ports, dhcp, or IPv6 issues. I’m not sure if this is a hardware or software issue, but from what I’ve read in searching I’m beginning to think it has something to do with IPv6 support. I’ve tried several live CDs (Knoppix, Ubuntu, Elive, etc) and all fail to connect me to the internet. Below is the output of several things I’ve tried (this is from Ubuntu Live):

```
 # mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok

$ ifconfig eth0
eth0	Link encap:Ethernet HWaddr 00:11:2F:8B:14:4D
	inet6 addr: fe80::211:2fff:fe8b:144d/64  Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:26 errors:0 dropped:0 overruns:0 frame:0
	TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
	Collisions:0 txqueulen:1000
        RX bytes: 3534 (3.4 KiB)	TX bytes:1334 (1.3 KiB)
	Interupt:19 Base address:0xc800

$ lspci  | grep Eth
0000:00:04.0 Ethernet controller: Silicon Intergrated Systems [SIS] SiS900 PCI Fast Ethernet (rev 90)

$ lsmod | grep mii
mii		5248 1 sis900

$ route –n
Kernel IP routing table
Destination 	Gateway	    Genmask	Flags Metric Ref 	Use Iface

# dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.

sit0: unkown hardware address type 776
sit0: unkown hardware address type 776
Listening on LPF/eth0 00:11:2f:8b:14:4d
Sending on LPF/eth0 00:11:2f:8b:14:4d
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

# dhcpcd eth0
dhcpcd: command not found

#ifup eth0
Ignoring unknown interface eth0=eth0


```

I really don’t know what any of those are telling me or doing, I just happen to find them as suggestions while searching for an answer.

Ubuntu seems to think I have two network cards, eth0 and eth1. When I look at my device manager/network adapters in XP the SiS900 is listed as well as something called 1394 Net Adapter. Not sure if this matters.


I’d really like to get a live distro at least connected to the internet prior to hd installation, if something were to go wrong with the install and I lose my xp partition I’ll have to look for help with my wife’s mac and she hates me to touch her computer. Any help would be much appreciated.

---

### Post by vasudevank on 2005-12-31
it looks like ifconfig realizes that there is a eth0, have you tried "ping -c 3 www.google.com" If you have proxy settings makesure those are configured. If ping works you should have some internet, also did you make sure that interface eth0 was activated and configured. If you have regular ethernet try also "net-setup eth0" otherwise if you have adsl try "adsl-setup" then "adsl-start". The last few codes are just a guess in Ubuntu

---

