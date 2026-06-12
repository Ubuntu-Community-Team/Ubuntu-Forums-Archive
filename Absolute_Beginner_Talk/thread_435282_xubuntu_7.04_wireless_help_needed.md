---
title: "xubuntu 7.04 wireless help needed"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by modified on 2007-05-06
I installed xubuntu for the first time last night and spent at least an hour trying to get the wireless to work. I'm on compaq presario laptop v2205us. There's a built in broadcom card. I have windows xp installed alongside and the wireless works in xp.

when i type 

sudo lshw
 description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 6
                bus info: pci@02:06.0
                logical name: eth1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:e0204000-e0205fff irq:20

sudo iwconfig
eth1      IEEE 802.11b/g  ESSID:"m"  Nickname:"modified"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Am I assuming correctly that xubuntu recognizes the card and has a driver for it? What should I check or do?

---

### Post by Twoism on 2007-05-06
I had the same problem too. When I installed Xubuntu on my laptop I couldn't access the internet.  Then I installed wifi-radar using Synaptic and it worked just fine.

---

