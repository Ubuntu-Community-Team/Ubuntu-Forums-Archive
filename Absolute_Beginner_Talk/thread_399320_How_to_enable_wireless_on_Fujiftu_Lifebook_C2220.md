---
title: "How to enable wireless on Fujiftu Lifebook C2220"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by avanrotciv on 2007-04-02
Hi,

I recently installed Ubuntu on my Fujitsu Lifeboook C2220, everything seems to be working ok but my the wireless, I've spent several hours reading through the help documents and haven't yet fond a solution to my problem.

The system seems to be recognizing the card and driver but it seems to be "disabled" and don't know how to enable it, here is a some of the info from the terminal after the code "lshw":

        *-network:1 DISABLED
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth2
             version: 02
             serial: 00:90:96:57:e9:c2
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:dc000000-dc001fff irq:11
..........

I've tried to do enable it from the "networking" utility that comes with ubuntu with no success.

Can anyone help me out? I'm really new to Linux.

---

### Post by mikeyphi on 2007-04-02
Have a look under SYSTEM - ADMINISTRATION - NETWORKING
highlight your card, select PROPERTIES and tick ENABLE THIS CONNECTION
then exit

---

### Post by avanrotciv on 2007-04-02
I have already tried that, no success :(

---

### Post by Dual Cortex on 2007-04-02
Can you please post the output of
> cat /etc/network/interfaces

---

