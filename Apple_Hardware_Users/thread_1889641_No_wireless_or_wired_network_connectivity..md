---
title: "No wireless or wired network connectivity."
date: 2011-12-01
forum: Apple Hardware Users
---

### Post by NickAppleton on 2011-12-01
Hi all,

I've just entered the world of Macs and the first thing I've done is tried to get Ubuntu up and running. I have installed 10.04 (amd64) and cannot get any network connectivity (wired or unwired) at all. I followed the installation guide here [https://help.ubuntu.com/community/MactelSuapportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSuapportTeam/AppleIntelInstallation) and am using option key to select the boot operating system.

Using lspci I can see the devices:

---
02:00.0 Ethernet Controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
03:00.0 Network Controller: Broadcom Corporation Device 4331 (rev 02)

But calls to ifconfig only show the loopback device and this "pan0" which googling reckons is bluetooth. I figure there is a driver which I need to get - but with no network connection on the machine itself, I'm not entirely sure how to do that.

Could anyone point me in the right direction to get either of the wired or wireless up and running?

The Mac is an 17 inch quad-core i7 (Model: A1297) (I'm very new to Macs - this is the first one I've owned so please let me know if I am lacking information).

---

### Post by bluexrider on 2011-12-01
to help diag the issue, please run this command in terminal and post the results.

sudo lshw -c network


Thanks

---

### Post by NickAppleton on 2011-12-01
lshw -c network

---
  *-network UNCLAIMED
    description: Ethernet controller
    product: NetXtreme BCM57765 Gigabit Ethernet PCIe
    vendor: Broadcom Corporation
    physical id: 0
    bus info: pci@000:02:00.0
    version: 10
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi msix pciexpress bus_master cap_list
    configuration: latency=0
    resources: memory:b0400000-b040ffff(prefetchable) memory:b0410000-b041ffff(prefetchable)
  *-network UNCLAIMED
    description: Network controller
    product: Broadcom Corporation
    vendor: Broadcom Corporation
    physical id: 0
    bus info: pci@000:03:00.0
    version: 02
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master_cap_list
    configuration: latency=0
    resources: memory:b0600000-b0603fff

Thanks!

---

### Post by bluexrider on 2011-12-01
it obvious there are no drivers installed to make the cards work, however there is a link here:

4331 

[http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html]("http://homepage.uibk.ac.at/%7Ec705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html")

I am unable to locate a set of drivers for the broadcom BCM57765

NEED ADDITIONAL HELP

---

### Post by NickAppleton on 2011-12-01
Thanks a lot for that, I'll post an update if I can get the wireless active.

---

### Post by bluexrider on 2011-12-01
HERE: found it, this is the 57765 driver

[http://www.broadcom.com/support/license.php?file=570x/linux-3.118k.zip](http://www.broadcom.com/support/license.php?file=570x/linux-3.118k.zip)

---

### Post by NickAppleton on 2011-12-01
You are a legend. I just downloaded the ethernet driver, built it, inserted it and everything is working perfectly.

Thanks for the quick replies!

---

### Post by bluexrider on 2011-12-01
Sweet.

Happy *buntu

Please mark this (SOLVED)

---

### Post by morkovka078 on 2012-04-03
> **NickAppleton said:**
> You are a legend. I just downloaded the ethernet driver, built it, inserted it and everything is working perfectly.

Thanks for the quick replies!

Hi there,
I'm a complete n00b and got the exact same issue. I've downloaded the driver (from another CPU and burnt it), but i have no clue how to build it and insert it (where?) and make the stuff works. Please, could you guide me through this ? Many thanks

PS Im also on ubuntu 10.04 and terminal showed me the EXACT same messages.

---

### Post by hughr2005 on 2012-04-04
Hi morkova078,

I don't actually have a mac running ubuntu to check this on, but I would guess that you have to cd in terminal to the directory of the extracted zip and run:

```

./configure
make
sudo make install

```

Hope that works.

---

