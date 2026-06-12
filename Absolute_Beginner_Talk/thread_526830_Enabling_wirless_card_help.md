---
title: "Enabling wirless card help"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by mbm8e on 2007-08-15
I'm new to Ubuntu. I'm pretty sure all that I need is a simple command to activate my card but i'm 

sudo lshw -C network yields...


 *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 03
       serial: 00:90:96:bd:d6:7f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-11-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:fafec000-fafedfff irq:5

---

### Post by wolfen69 on 2007-08-16
as far as i know, broadcom wireless needs ndiswrapper.(in synaptic) then you need the windows inf. file to install it. read this:[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

---

### Post by jamvegan on 2007-08-16
I have the exact same card, and I have never been able to get it to work with the default driver.  As the reply above suggests, I have to use ndiswrapper.

As an additional note, if you follow the ndiswrapper instructions and your card is enabled, but you can't make a connection, you might want to try using wifi-radar (available via Synaptic Package Manager).  For some reason I can't get a connection with Network Manager, but with wifi-radar it works great.

---

### Post by mbm8e on 2007-08-16
I have installed ndiswrapper and installed the drivers. I still can't get the wireless card to activate. Any other ideas?

---

