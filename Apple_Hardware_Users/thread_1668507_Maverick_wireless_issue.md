---
title: "Maverick wireless issue"
date: 2011-01-16
forum: Apple Hardware Users
---

### Post by devinoneill1 on 2011-01-16
I've been following every walk through and wireless thread I can find, but I'm still unable to get connected via wifi on my MBP 4,1.
Here's what I've got
lshw -C network
```

*-network               
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 05
       serial: 00:22:41:fc:5c:82
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:97300000-97303fff

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

Any help would be greatly appreciated, Thanks for looking even if you cant help

---

