---
title: "DWL650 not recognized by system"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by zapdos on 2007-03-30
Hi there,
I need a little help on how to use my wireless card on my laptop (running Xubutu Edgy 6.10).  According to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink?highlight=%28wireless%29") the DWL650 is supposed to work "out of the box."  However, it does not even show up in network manager.  Is it a case of missing drivers?

lspci output:
>  lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller


---

### Post by amd-64 on 2007-03-31
My DWL-G650 works out of the box in feisty, make sure you have the restricted drivers installed (Linux-restricted-modules-generic). Madwifi (Atheros) has the required drivers. 

The interface shows as ath0

EDIT: Just realized that DWL-650 and DWL-G650 are not the same chipsets.

---

### Post by Terry851 on 2007-04-01
See my post re: getting my DWL650 working.  In my situation, the wireless card was recognized by Ubuntu - it was not connecting to the access point.  I use Shared vs Open access on my wireless access point, and needed to prefix my WEP passkey with the 'restricted' keyword via the terminal (iwconfig). Also, I needed to enter the ESSID in the same case that I entered on the wireless access point - in my case, I used Mixed Case for the ESSID.  Finally, once I got the card connected to the access point, I needed to disable ipv6 to get access to web sites.  Read my post and see if that helps.  Good luck!

---

### Post by stchman on 2007-04-02
> **zapdos said:**
> Hi there,
I need a little help on how to use my wireless card on my laptop (running Xubutu Edgy 6.10).  According to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink?highlight=%28wireless%29") the DWL650 is supposed to work "out of the box."  However, it does not even show up in network manager.  Is it a case of missing drivers?

lspci output:

Yes, you must install the restricted kernel.  The restricted kernel is madwifi compatible for Atheros cards.

I have laid out a procedure to install madwifi drivers in Ubuntu.  It works in 6.10 as I used it on my laptop.  I also lay out how to get WEP and WPA/WPA2 setup as well.  Here is the procedure:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

I hope this helps.

---

