---
title: "no wifi after kernel update"
date: 2012-10-10
forum: Apple Hardware Users
---

### Post by yinnus on 2012-10-10
Here's my issue.  in order to get sound from my headphone jack i need to update the kernel.  wifi works fine out of the box with 12.04.1 but as soon as i update the kernel to anything newer than 3.2 my wifi flakes out. i can see the list of available networks but it wont connect.  i am using a 27 inch imac 12,2

oddly enough, i can use a usb dongle with no issues.

any ideas???

thanks

---

### Post by yinnus on 2012-10-11
here's my connection info.

---------

*-network
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 3c:07:54:1d:b8:04
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=57765-v1.37 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:a8400000-a840ffff memory:a8410000-a841ffff
  *-network
       description: Wireless interface
       product: AR9300 Wireless LAN adaptor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 7c:c3:a1:ae:17:f2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic firmware=N/A ip=192.168.1.114 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:a8600000-a861ffff memory:8f900000-8f90ffff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
Linux glen-iMac 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[ 0.548758] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[ 8.299465] [Firmware Bug]: ACPI(GFX0) defines _DOD but not _DOS

---

