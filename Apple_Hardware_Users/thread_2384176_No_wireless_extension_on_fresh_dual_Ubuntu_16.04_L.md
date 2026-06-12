---
title: "No wireless extension on fresh dual Ubuntu 16.04 LTS install"
date: 2018-02-03
forum: Apple Hardware Users
---

### Post by mitad on 2018-02-03
Hi, 
I have just installed Ubuntu 16.04 on an old macbook pro (2010) with dual OSX boot (through rEFInd). 
Wireless connection works on OSX however it is not showing up in Ubuntu at all, although ethernet connection works. I have tried various commands gathered around the web but nothing appears to work for me.

 Surely more informative than words, here are some facts:

$ cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"
Linux mmt-MacBookPro 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

$ iwconfig
```

lo        no wireless extensions.
enp3s0    no wireless extensions.
```

$ lshw -class network
```

 *-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d3200000-d3203fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: c8:bc:c8:91:02:36
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5764m-v3.38 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:d3100000-d310ffff
```

$ rfkill list
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

$ lsusb
```

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0237 Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

$ lspci -nnk | grep -iA2 net
```

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: b43-pci-bridge
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3
    Kernel modules: tg3
```

Many thanks for your help,

---

### Post by jeremy31 on 2018-02-03
*Thread moved to **Apple Hardware Users**.*
Have you tried ```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```
Then reboot

---

### Post by mitad on 2018-02-05
Thanks jeremy31 for the advice, 
the following made it: 

```
sudo apt-get update 
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-generic bcmwl-kernel-source

```

And a power-off restart (reboot wasn't enough).

Cheers

---

