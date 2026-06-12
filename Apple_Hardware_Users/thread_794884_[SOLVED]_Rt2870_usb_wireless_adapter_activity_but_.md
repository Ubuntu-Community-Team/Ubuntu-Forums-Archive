---
title: "[SOLVED] Rt2870 usb wireless adapter activity but no connection"
date: 2008-05-15
forum: Apple Hardware Users
---

### Post by a1234 on 2008-05-15
Have compiled from scratch he ralink driver for my usb adapter. It is showing activity and the networktoll is showing connection.

 root@a1234-laptop:/home/a1234/Desktop/Stuff/2008_0506_RT2870_Linux_STA_v1.3.0.0/os/linux# /sbin/ifconfig ra0 inet up
root@a1234-laptop:/home/a1234/Desktop/Stuff/2008_0506_RT2870_Linux_STA_v1.3.0.0/os/linux# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1f:5b:e7:1a:b8
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 00:02:6f:4b:8b:34
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2870 Wireless
root@a1234-laptop:/home/a1234/Desktop/Stuff/2008_0506_RT2870_Linux_STA_v1.3.0.0/os/linux# 

Network device:	ra0
Hardware address:	not available
IP address:	not available
Netmask:	not available
Broadcast:	not available
Multicast:	not available
MTU:	not available
Link speed:	not available
State:	not available
Transmitted packets:	3509
Transmission errors:	0
Received packets:	5067
Reception errors:	0
Collisions:	0
 
However I can not connect to the internet. Please advice.

---

