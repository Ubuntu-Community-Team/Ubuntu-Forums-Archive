---
title: "Wireless Card Not Working"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-10-22
Hey guys. I am currently running Ubuntu live on a machine I just built. I have one small problem. I pulled a wireless card out of another computer, but so far I am not getting anything. On my Xubuntu desktop, it picked the card up right away and began to work. But that is not the case now. I know that you are usually able to do alot more once it is installed, but can I make it work before? Thanks.

---

### Post by chuckyp on 2007-10-23
Some info on the card would help.

---

### Post by bigboy_pdb on 2007-10-23
In the terminal type "lshw" and post the information under the sections that have "network" in the name, or if you know the chip set for the card then just post that.

---

### Post by drndrw on 2007-10-23
```
description: Wireless Interface
product: AR5212 802.11abg NIC
vendor: Antheros Communications, Inc.
physical id: b
bus info: pci@00:0b.0
logical name: wifi0
version: 01
serial: 00:0f:a3:1b:72:3e
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
resources: iomemory:feae0000-feaeffff irq:19
```

Well, now I know that it's working, because it picks up other networks in my area. But whenever I try to get a computer working with my connection, it never does. Why is this? I have a Netgear router if it helps.

---

