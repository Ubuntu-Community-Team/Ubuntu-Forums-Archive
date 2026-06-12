---
title: "network connection"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by kv_abhiram on 2007-08-13
I am using BSNL broaband internet from India and I have been provided with an internal ADSL Modem that is from a company called "sasken".
and I am not able to use my Sasken Modem for Internet connectivity which is a PPPoE modem.
I tried sudo PPPOEconf and it said that either my ethernet connections were not completely connected or that some other pppoe connection is controlling my internet card.

---

### Post by kv_abhiram on 2007-08-13
DETAILS OF THE MODEM  I have 




*-network:0 UNCLAIMED 
description: Network controller 
physical id: 9 
bus info: pci@00:09.0 
version: 01 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list 
configuration: latency=64 maxlatency=16 mingnt=1 
resources: iomemory:febf0000-febfffff irq:11 
*-network:1 
description: Ethernet interface 
product: VT6102 [Rhine-II] 
vendor: VIA Technologies, Inc. 
physical id: 12 
bus info: pci@00:12.0 
logical name: eth0 
version: 78 
serial: 00:16:ec:94:e4:d2 
size: 10MB/s 
capacity: 100MB/s 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s 
resources: ioport:ee00-eeff iomemory:febef800-febef8ff irq:18
__________________

---

### Post by nvrpunk on 2007-08-13
sudo lsmod,  see if the module for the card is loaded.  If you dont know what it is, google for it.  I have no actual familiarity with that card but if you have a module loaded for it you should be able to configure it.

---

### Post by kv_abhiram on 2007-08-13
sry im not able to figure that out

---

### Post by kv_abhiram on 2007-08-14
heLLLooo
this is serious
im not able to configure my BSNL broadband connection
i hav an internal PCI modem whose cfg. is as mentioned above
 plzz HELP

---

### Post by steve-shinn on 2007-08-14
> **kv_abhiram said:**
> heLLLooo
this is serious
im not able to configure my BSNL broadband connection
i hav an internal PCI modem whose cfg. is as mentioned above
 plzz HELP


Can you not access the modem through firefox by typing in the default IP address of the modem .... it is likely to be in the range 192.168.1.1 through to 191.168.1.199

---

### Post by kv_abhiram on 2007-08-14
actually i have an internal PCI modem
so... CANT

---

### Post by kv_abhiram on 2007-08-15
any body ...can tell me how to configure ???

---

