---
title: "weird wifi problem."
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2006-07-18
i recently tried setting up my wifi card in my compaq evo n600c laptop and i got the wifi to work. but then when i rebooted it sometimes works, and sometimes dosent. and also when i check out my network settings everrrythingg sais "the interface is not configured" but im on the internet rite now when im wired to my router, so somthings gota be working but somthing is definitly wrong. any ideahs? thanks


more info:
 wifi card- linksys wpc54g (broadcom 4313)

lspci-
 
 mike@mike-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:03.0 CardBus bridge: Texas Instruments PCI1420
0000:02:03.1 CardBus bridge: Texas Instruments PCI1420
0000:02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
0000:02:09.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
0000:03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by OpsVentus on 2006-07-19
Hello da1nonlymikeo,

How did you configure your wireless network?
Is everything on auto? Becauss that could explain why it sometime works.
To make it more "stable" use Ubuntu's network-manager to set your wireless LAN.

Cheers,
Bart.

---

