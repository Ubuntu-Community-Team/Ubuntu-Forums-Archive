---
title: "how to get madwifi into Restricted Drivers Manager"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by halfhearted on 2008-02-08
Is madwifi available as a "restricted driver" in Ubuntu? If so how do I get it? Where do I find it? Once it is listed in the Restricted Drivers Manager I understand that I can install it easily. Thanks for any assistance.

---

### Post by halfhearted on 2008-02-08
This is what I get when I use lspci -

user1@user1-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
07:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a02 (rev 03)
user1@user1-laptop:~$ 

The wifi PCMCIA card is seen as -
07:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a02 (rev 03)
at least I think that that is it. The card is actually an ealy version of the Belkin N1 mimo. The part number is F5D8011 and the version number is 1000. According to this web site -
[http://www.newegg.com/Product/Product.aspx?Item=N82E16839314001](http://www.newegg.com/Product/Product.aspx?Item=N82E16839314001)
"...There are two versions of this card. The F5D8011 v1000 is based on the Atheros XSPAN chipset. The newer v2000 card uses the Marvell TopDog chipset..." So, I have the older version and an Atheros XSPAN chip set. Is that good or bad? How do I tell? Thanks for any help.

---

### Post by Galdor on 2008-07-10
Hi,
I have a new card with AR5008E Chipset
(XSPAN PCI express)

I have in lsPCI:

...
Network Controller: Atheros Communication Corporations Inc. AR5418 802.11abg Wireless PCI Express Adapter

I have loaded with modprobe:
ath_pci
ath_hal
ath_rate_sample

DMESG says:
ath_hal 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, F5413)

It seems, linux-restricted-modules(-2.6.22-14-generic)
does not support Chipset generation 8 WLAN Adapter Cards

I guess a standallone install of madwifi would bring it up to work.
the problem is, this versions could conflict and is currently not included in Ubuntu (/.10) standards, what decreases ease of handling .

so far
:(

---

