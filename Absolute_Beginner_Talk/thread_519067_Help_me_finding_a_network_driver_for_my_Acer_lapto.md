---
title: "Help me finding a network driver for my Acer laptop"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-08-06
Hi all

I have an Acer laptop. On the machine there is a sticker saying:

"Mobile Intel 940 GML Express Chipset"

This is the network card, right? I am trying to find the driver for it and use it in Ndiswrapper, but it won't work. Can anyone help me? :)

---

### Post by Dr Small on 2007-08-06
Greetings Wikzon, fancy seeing you here :P
Maybe some of the other fellas can help better than I ;)

Dr Small

---

### Post by Wikzo on 2007-08-06
Off topic: Long time no see Dr Small :)

---

### Post by annda on 2007-08-06
nope, it's not a network card. what exactly is the Acer model? can you post the output of those commands:

```
lspci
```

and 

```
lshw -C network
```

---

### Post by Wikzo on 2007-08-06
Ah ... ok.

> wikzo@wikzo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


> wikzo@wikzo-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:8c:3b:3a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A ip=86.52.46.176 latency=0 multicast=yes
       resources: iomemory:34000000-34003fff ioport:2000-20ff irq:16
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0a:03.0
       logical name: eth1
       version: 02
       serial: 00:16:cf:7b:37:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=96 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0100000-d0101fff irq:18


I can use the wired network right out of the box (I am online right now), but wireless won't work :'(

---

### Post by annda on 2007-08-06
there's a guide for your Broadcom 4318:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d)

---

### Post by ugm6hr on 2007-08-06
Assuming you are asking how to get wifi working - this is your wifi card:
> 0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I believe ndiswrapper is the best option to get this working (see the comment in this re: native driver instability: [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)).

So potential solutions (take your pick):
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by lgambett on 2007-08-06
I have an Acer like you. I was forced to use Ndiswrapper until the release of Feisty; with feisty your WiFi card is supported natively, provided that you install the bcm43xx-fwcutter package. For (I think) copyright policies Broadcom firmware is not included natively in Feisty.

---

### Post by Wikzo on 2007-08-06
> **annda said:**
> there's a guide for your Broadcom 4318:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d)

Yepeee ... it works!! Thanks for the guide :D

---

