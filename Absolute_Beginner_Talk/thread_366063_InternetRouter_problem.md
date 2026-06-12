---
title: "Internet/Router problem"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by kaka0502 on 2007-02-20
I newly switched to ubuntu. I installed Ubuntu 6.06 and the internet doesnt work. I tried pinging 192.168.1.1 (Router) but no use. I disabled IPv6 options in firefox and system wide by changing the ipv6 line in /etc/modprobe.d/alises and even tried making static ip. I have XP  dual boot in which internet works fine. 

Here is output for ifconfig and lspci


genome@Genome:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:A1:C8:6F
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fea1:c86f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:675 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:331867 (324.0 KiB)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39173 (38.2 KiB)  TX bytes:39173 (38.2 KiB)

genome@Genome:~$
genome@Genome:~$ lspci
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev:03:0a.0 Communication controller: Agere Systems: Unknown device 0620

Can someone help me with this? Thank You in advance.

---

### Post by kaka0502 on 2007-02-20
Any genius out there to help me.

---

### Post by annda on 2007-02-20
sorry, not a genius. but i for one am a bit  thrown off by the following:

> inet addr:192.168.1.2

it looks like you get and IP on your ethernet (eth0) and should be able to communicate with the rest of the net.

i do not understand. anybody does? has anyone seen this before?

EDIT: i don't see an Ethernet controller in your lspci output. that is strange... how do you connect to the internet?

---

### Post by kaka0502 on 2007-02-20
I read on some other post to configure dhcp to static ip manually. So I did as it was mentioned. because of that it is showing that ip. Before that there was no such field as inet at all. This is what I see after switching back to dhcp.

genome@Genome:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:A1:C8:6F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2772 (2.7 KiB)  TX bytes:2772 (2.7 KiB)

---

### Post by annda on 2007-02-20
so it's possible you do not have a working network card at all?

please tell us what hardware you have (ethernet card i suppose) - make, model etc., anything you know.

also, if you have time to seriously deal with that, there is an excellent guide here:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

a bit overkill for most users, but there are tons of suggestions.

---

### Post by kaka0502 on 2007-02-20
Annda, I went through the wireless troubleshootingguide. Actually I am connected through wire. Still, the guide was helpful to some extent. I found lshw command to listen to hardware. I find some thing like this when I used static ip

> bridge
description: 	Ethernet interface
product: 	MCP51 Ethernet Controller
vendor: 	nVidia Corporation
physical id: 	14
bus info: 	pci@00:14.0
logical name: 	eth0
version: 	a3
serial: 	00:17:31:a1:c8:6f
size: 
capacity: 
width: 	32 bits
clock: 	66MHz
capabilities: 	bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration:	
autonegociation	=	on
broadcast	=	yes
driver	=	forcedeth
driverversion	=	0.48
duplex	=	half
ip	=	192.168.1.2
link	=	no
multicast	=	yes
port	=	MII
speed	=	10MB/s
resources:	
iomemory	:	fe02b000-fe02bfff
ioport	:	f200-f207
irq	:	201

When using DHCP it is 

> bridge
description: 	Ethernet interface
product: 	MCP51 Ethernet Controller
vendor: 	nVidia Corporation
physical id: 	14
bus info: 	pci@00:14.0
logical name: 	eth0
version: 	a3
serial: 	00:17:31:a1:c8:6f
size: 	10000000
capacity: 	100000000
width: 	32 bits
clock: 	66MHz
capabilities: 	bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration:	
autonegociation	=	on
broadcast	=	yes
driver	=	forcedeth
driverversion	=	0.48
duplex	=	half
link	=	no
multicast	=	yes
port	=	MII
speed	=	10MB/s
resources:	
iomemory	:	fe02b000-fe02bfff
ioport	:	f200-f207
irq	:	201

The only difference between the two is ip address, which in the static ip case was manually configured by me. I could see eth0 network adapter in my Network Settings. I do not know what a bridge does. As it is mentioned above instead of Ethernet Controller.  This is what I found about bridge.
Class	    Description	                     Examples
-----------------------------------------------------------------------------------------------------------
bridge	   internal bus converter 	PCI-to-PCI brige, AGP bridge, PCMCIA controler, host bridge
Do you have any suggestions?

---

### Post by kaka0502 on 2007-02-20
I found a different thread having the same problem as me.

[http://www.linuxforums.org/forum/linux-networking/65765-cannot-get-dhcp-work-ubuntu.html](http://www.linuxforums.org/forum/linux-networking/65765-cannot-get-dhcp-work-ubuntu.html)

The solution they give is to upgrade to 6.10. Should try that. got any Suggestions?

---

