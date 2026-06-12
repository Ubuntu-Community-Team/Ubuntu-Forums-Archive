---
title: "need help getting wifi to work (dell b130/1300)"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by econobeing on 2006-08-25
so far this has been the biggest problem for me, i've had ubuntu installed since sunday, and fixed most of my problems, but this one has persisted...

i've tried just about every guide i can find but none of them works, in fact, before i tried anything when i would go to System > Administration > Networking i could see my card there, eth0 or eth1, i forget which. but now even that isn't there...

so i need a way to reset everything i screwed up trying to get it to work, and i need some help on how to get it to work. hopefully if i make my own topic, if something goes awry with the instructions i'm given i can post it, instructions tailored to me, etc.

as most likely suspected the card is made by broadcom, the model i'm not to sure of, after i post this i'm going to go back into windows and see if i can find out more about it.

can somebody help me please? :frown:

---

### Post by econobeing on 2006-08-25
this is all i could really find...:

GENERAL:
Dell Wireless 1470 dual band WLAN Mini-PCI card

Device type: Network adapters
Manufacturere: Broadcom
Location: PCI bus 2, device 3, function 0

DRIVER:
Driver Provider: Broadcom
Driver Date: 11/2/2005
Driver Version: 4.10.40.0
Digital signmer: Microsoft Windows Hardware Compatability Publisher

---

### Post by DavidFourer on 2006-08-25
I have the same Broadcom 1470 in Dell computer. I go to system > admin > networking
I get eth1 wireless (setup) (activate)
under setup I get the following questions, which I don't know anything about:

Configuration:
IP Address:
Subnet mask:
Gateway address:
ESSID:
Key type:
Wep Key:

I thought it would search the airwaves and tell me what wireless signals were available (like a Windows or Mac system).  Is there a way to do this?  If not, what do I need to know?  I'm on a cable at the moment.

---

### Post by DavidFourer on 2006-08-25
I checked  WifiDocs/WirelessCardsSupported
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Regarding  Dell   Wireless 1370 802.11bg  Broadcom 4318 

Ships with Celeron model Inspiron 1300. Tried ndiswrapper and firmware methods linked [WWW] [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear). lspci reports: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). Card starts up but cannot find any way to connect to network with dapper

Does this mean I should give up now?
Any more info on this?

---

