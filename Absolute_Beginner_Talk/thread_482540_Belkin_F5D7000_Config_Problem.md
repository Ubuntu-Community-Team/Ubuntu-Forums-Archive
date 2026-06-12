---
title: "Belkin F5D7000 Config Problem"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by hdensley on 2007-06-23
-I have installed ndiswrapper
-not sure what chipset I have, but I have a different INF file than many who have installed this 'BLKWGDv7.inf'
- this INF file will not show up in Systems->Administration->Wireless Windows Drivers, although it seems to think it's installed
- wireless is not working, but shows, as per below


harold@harold-desktop:~$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 9
       bus info: pci@00:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:e000-e0ff iomemory:ef008000-ef0081ff irq:11
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: 10
       serial: 00:20:ed:70:90:83
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.102 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:e400-e4ff iomemory:ef009000-ef0090ff irq:20

---

