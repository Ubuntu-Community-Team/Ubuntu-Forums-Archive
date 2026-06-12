---
title: "No wireless network after upgrade to 11.10 Oneiric on MacBook Pro 1,1"
date: 2011-10-15
forum: Apple Hardware Users
---

### Post by matthorr on 2011-10-15
After upgrading from Natty to Oneiric on my MacBookPro 1,1 I can no longer connect to wireless networks.

I can open Systems Settings, Network and select Wireless.  I can see the MAC address and all the networks in the area in the drop down menu.  However, when I select my network it looks like it quickly connects and then immediately disconnects every time.  If I select Use as Hotspot, it works until I open and close the Configuration window (when it promptly disconnect whether I make changes or not).

I can use the wired network no problem (although I do not get any indicator in the upper right of the screen for wired or wireless except with the guest account).

Any suggestions on how to troubleshoot?

---

### Post by matthorr on 2011-10-16
Here is some more info after running "lshw -C network":

*-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cb:08:2d:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:98100000-9810ffff

---

