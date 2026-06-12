---
title: "Wireless Network on Macbook 4,1"
date: 2009-11-23
forum: Apple Hardware Users
---

### Post by renegadespork on 2009-11-23
As always, I was very hesitant to start a new thread about my issue, but it seems I have exhausted my searching capabilities on the forums, so this seems to be my last option. Perhaps my problems has already been solved, but I'm not really knowledgeable enough to know exactly what is causing my problem to know what solution to look for. 

Essentially, here's my issue:

I recently installed Ubuntu 9.10 on my Macbook 4,1 model (the first time I've used any sort of linux), and everything is working great. The only problem I seem to have is that I can't get it to recognize any wireless networks. I assume it's a driver issue, because I have been unsuccessful in finding/installing a driver for my wireless card. 

I typed ```
lspci
``` in the terminal to find my wireless card model, and it is a ```
Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```When I open up the System -> Administration -> Hardware Drivers, it says "No propriatary drivers are in use on this system".

If you know of what drivers I need to download/install/activate, or if you need more information to assess my problem, I would really appreciate the help.

EDIT:
A little more info:
```
jesse@Jesse-Laptop:~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:90500000-90503fff memory:90000000-900fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:22:41:3a:f7:96
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:90400000-90403fff ioport:5000(size=256) memory:90800000-9081ffff(prefetchable)

```

---

