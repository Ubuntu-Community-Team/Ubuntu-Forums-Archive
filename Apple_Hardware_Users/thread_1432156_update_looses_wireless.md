---
title: "update looses wireless"
date: 2010-03-17
forum: Apple Hardware Users
---

### Post by Colinwlu on 2010-03-17
Update manager installed some security updates and other stuff and now I've lost my wireless connection.

I have an iMac G5 running ubuntu 9.10 via a firewire drive. When I tried running OS X Leopard I had to reboot my O2 router to get it working.  I've tried that in ubuntu but doesn't work. I've uninstalled/reinstalled b43-fwcutter & wireless-tools but still doesn't work.  It just keeps asking for the wep pass code. sudo lshw -C network displays the following.

****@****:~$ sudo lshw -C network
[sudo] password for ****: 
  *-network               
       description: Ethernet interface
       product: Shasta (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0001:03:0f.0
       logical name: eth0
       version: 00
       serial: 00:0d:93:5b:0c:da
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.1.65 latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100MB/s
       resources: irq:40 memory:80400000-805fffff memory:80200000-802fffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0001:01:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=16
       resources: irq:60 memory:80084000-80085fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:0a:95:f8:6f:83
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
****@****:~$ 

Any ideas anyone?

---

### Post by Colinwlu on 2010-03-17
Hour later it suddenly decides to connect!!!!!!!!!!

---

