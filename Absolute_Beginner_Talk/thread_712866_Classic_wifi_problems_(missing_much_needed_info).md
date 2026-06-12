---
title: "Classic wifi problems (missing much needed info)"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by lible on 2008-03-02
Currently running Unbuntu 7.10

I'm Attempting to connect to wireless network but no luck.. here is all  the info i could gather on my problem. p.s. i am totally new to linux.

```
-network DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 02
                serial: 00:16:b6:57:c4:1c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

 0280: 14e4:4318 (rev 02)

```

Wireless Card: Lynksys pci with speedbooster
Drivers im using are: bcmwl5.sys / WMP54GS.inf (original CD from vendor) Also attempted with drivers from website.

I used this guide to attempt setup
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
I used the Gutsy version ndiswrapper
tried gui install and through commands when gui didint work.

When i install driver using GUI it says hadware is installed.

This is my second attempt, My first install i used ndiswrapper 1.52 (not sure of which tutorial) did a new install of unbuntu for the current information. 

Appreciate any help! ive been trying this for 2 days

---

### Post by erginemr on 2008-03-02
There is an excellent howto run by **kevdog:**
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

which I know has saved many lives. I think you should read his howto first, and ask him a question if you cannot find your way out.

---

