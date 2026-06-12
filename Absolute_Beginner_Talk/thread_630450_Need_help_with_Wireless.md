---
title: "Need help with Wireless"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by chadefa1 on 2007-12-03
Hi,

I guess I am really lost with setting up my wireless. I have a Dell Inspiron B130. I wanted to find out what wireless card I have, so I typed:```
 sudo lshw 
``` and here is what I got in the output: 
>  *-network:1 DISABLED
                description: Wireless interface
                product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 02
                serial: 00:14:a5:38:69:e8
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


So, I guess that the problem is that the wireless interface is disabled. 

Another thing is, if i launch wifi-radar, I get the following in the terminal:

> eth1      Interface doesn't support scanning : No such device

In general, I can't seem to detect any wireless network (although windows picks them up well). Any assistance will be greatly appreciated: steps I should take, things I should try (please, no technical talk. If I need to install a driver, please tell me how to find which one, ...)

Thanks!
Tom

---

### Post by Griffiss on 2007-12-03
Have a look at this: [http://ubuntuforums.org/showthread.php?t=405990&highlight=BCM4311](http://ubuntuforums.org/showthread.php?t=405990&highlight=BCM4311)

It's a howto for your type of wireless card (Broadcom BCM4311)

---

### Post by anewguy on 2007-12-03
Some may suggest you use the restricted driver for Broadcom chipsets, however I would point you to this instead:

[http://ubuntuforums.org/showthread.php?t=507505]("http://ubuntuforums.org/showthread.php?t=507505")

Some of things have changed slightly since 7.04 and 7.10 were introduced.  Basically, if you have a wired connection, use synaptic package manager to install ndiswrapper and the ndiswrapper utilities, then follow the 1st section of the above link to download the driver you will need, blacklist the existing driver and then install the driver that will work.

Post back if you need some more help!:)

---

