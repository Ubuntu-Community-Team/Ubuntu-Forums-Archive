---
title: "Stubborn Wireless Card"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by lepban on 2007-02-10
Hey there guys, I have been having a little bit of trouble getting my Wireless card to work.

The funny thing is it worked just fine the last time i installed Edgy.  But not in the most recent installation. 

When i go to wireless connection properties my connection eth1 has no signal (about 2 ft from router) and shows a "disconnected" status

this is my lshw

>  *-network:0 DISABLED
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@03:02.0
                logical name: eth1
                version: 03
                serial: 00:90:4b:a5:a8:63
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx ip=192.168.2.88 multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:b0204000-b0205fff irq:177


i am concerned with the network:0 disabled bit

My card is a Broadcom 4306 and the current driver came off the Driver cd bcmwl5

Any advice is appreciated   Please and Thank you
-lep

---

