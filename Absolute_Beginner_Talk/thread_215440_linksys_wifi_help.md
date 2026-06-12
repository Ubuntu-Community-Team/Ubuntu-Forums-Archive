---
title: "linksys wifi help?"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2006-07-13
i have a Hp compaq evo n600c laptop and im using a linksys WPC54G ver.3 wifi card. i downloaded kwifi manager and wifi radar from add/remove but i cant seem to connect to internet. can anyone help me out? thanks

more system info.

 ethernet card: ler: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42) 

motherboardchipset: dge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04) 
dge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04) 

cpu: Intel(R) Pentium(R) III Mobile CPU      1200MHz

---

### Post by rbalfour on 2006-07-14
can you post the output from the following command.

$ sudo lspci

---

### Post by da1nonlymikeo on 2006-07-14
heres the reply from sudo lspci



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
root@mike-laptop:~#

---

### Post by rbalfour on 2006-07-14
Here is your wireless card -> 0000:03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Here is your onboard ethernet card -> 0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)

Does the onboard card work?

---

