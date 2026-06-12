---
title: "New to everything...wireless"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by japribik on 2007-08-05
I am from windows, new to linux.  I need a super dumb dumb guide to figuring out how to get my wireless network device to work.  What do I have to do to 1. make sure my device is compatible and 2. connect to the wireless network?

---

### Post by overdrank on 2007-08-05
> **japribik said:**
> I am from windows, new to linux.  I need a super dumb dumb guide to figuring out how to get my wireless network device to work.  What do I have to do to 1. make sure my device is compatible and 2. connect to the wireless network?

HI and welcome, could you give us some info on the wireless device. You can use the command  lspci in the terminal located under applications,accessories, terminal and paste the output here and maybe we can help.

---

### Post by japribik on 2007-08-05
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller0000:05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller


:confused:

---

### Post by overdrank on 2007-08-05
> **japribik said:**
> 0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[COLOR="Red"]0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
0000:05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller0000:05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller


:confused:

Hi, ok your wireless card is highlighted and it can be used although it will require some work.
This is one link of many 
[http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom+Corporation+BCM4318](http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom+Corporation+BCM4318)
And here is the search that contains the rest
[http://ubuntuforums.org/search.php?searchid=24930487](http://ubuntuforums.org/search.php?searchid=24930487)
It can be done as it has help many but you may want to take small steps and keep a positive attitude. Good luck! :popcorn:

---

### Post by japribik on 2007-08-06
awesome! works perfectly.

thanks

---

### Post by overdrank on 2007-08-06
> **japribik said:**
> awesome! works perfectly.

thanks

Great glad to hear and can you mark the thread as solved, 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Thanks and good luck! :popcorn:

---

