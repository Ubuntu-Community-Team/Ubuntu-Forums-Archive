---
title: "Installing Madwifi"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Squee__x on 2008-02-02
I want to be able to use wireless network with Ubuntu, but I'm really new to it and I don't have a clue how to install Madwifi
Anyone got any idea? :confused:
Thanks
xx

---

### Post by Masteroc on 2008-02-02
Ubuntu 7.1 has madwifi preinstalled as far as i know

---

### Post by ugm6hr on 2008-02-02
Not sure how much you know about Linux....

If you need madwifi - it is in the Ubuntu Restricted Drivers.  Just update Ubuntu, then load the restricted drivers.

Make sure you have an Atheros wifi card that is supported first though...

---

### Post by Squee__x on 2008-02-02
> **ugm6hr said:**
> Not sure how much you know about Linux....

If you need madwifi - it is in the Ubuntu Restricted Drivers.  Just update Ubuntu, then load the restricted drivers.

Make sure you have an Atheros wifi card that is supported first though...

I updated Ubuntu, but it's not in Restricted Drivers, and it says on the Madwifi website, that my card is supported.
I actually don't have a clue ;|
x

---

### Post by ugm6hr on 2008-02-03
> **Squee__x said:**
> I updated Ubuntu, but it's not in Restricted Drivers, and it says on the Madwifi website, that my card is supported.
I actually don't have a clue ;|
x

Start from the beginning - post the output from:
```
lspci
lshw -C network
```

These will confirm your card chipset before we go down the route of manually installing madwifi (which is easy enough).  Double-check that it is supported.  Then download the latest madwifi (0.9.3.3) - then follow this advice: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu) 
How to install madwifi is given in the madwifi readme.  Just double-click on the download to extract.

If it doesn't make sense - just ask.

---

### Post by Squee__x on 2008-02-17
> **ugm6hr said:**
> Start from the beginning - post the output from:
```
lspci
lshw -C network
```

These will confirm your card chipset before we go down the route of manually installing madwifi (which is easy enough).  Double-check that it is supported.  Then download the latest madwifi (0.9.3.3) - then follow this advice: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu) 
How to install madwifi is given in the madwifi readme.  Just double-click on the download to extract.

If it doesn't make sense - just ask.

Output:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
06:05.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
06:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
rebecca@rebecca-laptop:~$ lshw -C network


That's it
Sorry I took so long to post. I think I found it in Restricted drivers and it's enabled, but it still won't let me connect to wireless :/

---

