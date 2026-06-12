---
title: "Wireless configuration, driver is good now though =)"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by nsimeone2000 on 2008-02-18
Well Golem had helped me out with a really nice install on my wireless driver, now I see that it is on, it is in my network managers, but I cannot find any "hotspots" if you will with it, nor can I connect to my own.

In my neighborhood there is like 7 though, so I could really care less about connecting to my own, but one of them would be super cool :)

When I run:
lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
      [COLOR="Red"] logical name: eth1[/COLOR]
       version: 01
       serial: 00:1a:73:0d:cb:07
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,03/23/2006, 4.40.19.0 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:b6000000-b6003fff irq:9

So I know the drivers are installed, but the problem I am thinking is the fact that the logical name is eth1 and not something like wlan0.  Might be a longshot but yea, thats what I was thinking.

I found a really good how to guide that works in terminal to manually configure it, but for some reason the DHCPOFFERS are never accepted, I don't really know what thats all about.

I am not really familiar with anything besides terminal at this point.  This might be way easy to fix, I think I am overthinking it though.

Thanks

---

### Post by nsimeone2000 on 2008-02-18
Bleh, nevermind I figured it out.

---

