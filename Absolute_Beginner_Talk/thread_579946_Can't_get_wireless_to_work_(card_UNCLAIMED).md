---
title: "Can't get wireless to work (card UNCLAIMED)"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by klaasvanschelven on 2007-10-18
Hi all,

I'm trying to get wireless to work on my girlfriends laptop - a Lenovo Thinkpad T60. I'm a big fan of Linux in general and Ubuntu in particalur, but this has been a pain all way through.... anyway, my current point of stuckness is the wireless. 


I've installed both
linux-restricted-modules for my kernel and
madwifi-tools "tools for the Multiband Atheros Driver for WiFi"

I have Ubuntu 7.10 (yes I know I'm a day early, but it's the only thing that I got to work to some degree).

This is what lshw has to say:

klaas@thinkpad:~$ sudo lshw -C network
[sudo] password for klaas:
*-network
description: Ethernet interface
product: 82573L Gigabit Ethernet Controller
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 00
serial: 00:1a:6b:67:85:ca
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.2.102 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
*-network UNCLAIMED
description: Network controller
product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list
configuration: latency=0

I have no idea what this means "UNCLAIMED" (the Ubuntu wirless guide has explaining it as a TODO). The weird thing is, that if I reboot without a plugged in CAT-5, Ethernet interface too....


Help would be very much appreciated - I've been working an evening on getting the graphics to work and still have no sound. 




[SIZE="1"](I posted about this earlier here  - [http://ubuntuforums.org/showthread.php?p=3552369#post3552369](http://ubuntuforums.org/showthread.php?p=3552369#post3552369))[/SIZE]

---

### Post by klaasvanschelven on 2007-10-19
For those who happen to wander into this at a later date:

The AR5418 Atheros turns out to be in the 5008 / AR5008 series. As of yet not supported by any Ubuntu version, since it's not released in the driver project (madwifi) yet. Search for installing this driver (madwifi) from the subversion trunk - this should get you a bit further - I'm having it work now, just not stable (usually works for a couple of minutes in a row).

---

