---
title: "Wireless unassociated"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by fattysfinest on 2008-01-04
Hi all, still very new at this so go easy on me please.
I,m trying to get my wireless to work on this laptop. ubuntu 7.04.
I ran lshw and found the following.
It seems like everything is ok except ireless unassociated.
How do I associate it
Thanks for any help, 
Brian
 *-network:1
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@01:02.0
                logical name: eth1
                version: 04
                serial: 00:0c:f1:03:f7:79
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=128 maxlatency=34 mingnt=2 multicast=yes wireless=unassociated

---

### Post by spiderbatdad on 2008-01-04
looks like you just need to try and manually configure the settings. This can be done by clicking on the network monitor applet in your panel.

---

