---
title: "Wireless help in Ubuntu 6.10"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by elishabet on 2007-01-13
The problem:  I cannot get the wireless to work.  I can connect via an ethernet cable, just not over the wireless. I have the correct ESSID in the Network Settings window, but I think there may be some problems with that.  I've tried everything I can, and would appreciate any help.

The computer: It's a Compaq Presario M2000 (laptop), the address is DHCP. 
I can ping my local loopback device, but not the router.  I don't know terribly much about Linux, but I can follow instructions and would appreciate any help.

lshw:
	 *> -network:1 DISABLED
	                description: Wireless interface
	                product: BCM4306 802.11b/g Wireless LAN Controller
	                vendor: Broadcom Corporation
	                physical id: 6
	                bus info: pci@02:06.0
	                logical name: eth1
	                version: 03
	                serial: 00:90:4b:af:7b:da
	                width: 32 bits
	                clock: 33MHz
	                capabilities: bus_master ethernet physical wireless
	                configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
	                resources: iomemory:e0204000-e0205fff irq:185

iwconfig:

	> lo        no wireless extensions.
	
	eth0      no wireless extensions.
	
	eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
	          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
	          RTS thr:off   Fragment thr:off
	          Encryption key:off
	          Link Quality:0  Signal level:0  Noise level:0
	          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
	          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

	sit0      no wireless extensions.

dhclient eth1:

	> SIOCSIFFLAGS: No such file or directory
	SIOCSIFFLAGS: No such file or directory
	Listening on LPF/eth1/00:90:4b:af:7b:da
	Sending on   LPF/eth1/00:90:4b:af:7b:da
	Sending on   Socket/fallback
	receive_packet failed on eth1: Network is down
	DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
	send_packet: Network is down

iwlist eth1 scan:
	> eth1      Interface doesn't support scanning : No such device

---

### Post by oyvindaa on 2007-01-14
I've no experience with this kind of thing, since my card worked out of the box, but maybe you'll find [this](http://ubuntuforums.org/showthread.php?t=185174) one helpful.

---

### Post by elishabet on 2007-01-14
Thank you for your advice.

I hadn't found that before, but I tried it and the wireless still doesn't work.

But I appreciate you trying..

---

### Post by elishabet on 2007-01-16
Bump?

Can anyone help?

---

### Post by speedothebrief on 2007-03-17
argh... me too...
my laptop: no problems...
my desktop: lots of problems.

I can't seem to use
```
sudo iwlist eth1 scan
```
either.

GAR!

---

### Post by Skidpad on 2007-03-17
> **speedothebrief said:**
> argh... me too...
my laptop: no problems...
my desktop: lots of problems.

I can't seem to use
```
sudo iwlist eth1 scan
```
either.

GAR!

For what it's worth people, during setup for my wireless card I had to "configure" the connection as "**ra0**", not eth1.  Have any of you tried changing that configuration?  eth1 is my wired connection.  

I get the same "doesn't support scanning" if I "sudo iwlist eth1 scan" as you folks, but if I "sudo iwlist ra0 scan", it works fine and my wireless card and network show up correctly identified.

This is on a 4 yr old Compaq 2135US laptop with an ASUS WL-107G wireless pcmcia card.



**elishabet** Your wireless interface says "disabled".  Is this connection "checked" in the Network Settings window?

---

### Post by Dizturbanz on 2007-03-17
Hi Elizabeth,

Just went trough some painful lessons as a new by but I just got my wireless network up and running. I've posted the steps I went through on [http://ubuntuforums.org/showthread.php?t=386669](http://ubuntuforums.org/showthread.php?t=386669)

Maybe it helps....
good luck

---

### Post by cwmaxson on 2007-03-17
I think this will work for your wireless card which I assume is a Broadcom 4306.  BCM43xx cutter seems to not work at all, but I use ndiswrapper and it works like a charm.  

[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper)

Also, this thread recommends network manager, I use WICD because it seems to do more of what it's supposed to:
[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Hope this helps.

---

