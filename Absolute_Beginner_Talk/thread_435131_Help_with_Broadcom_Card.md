---
title: "Help with Broadcom Card"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by dylan623 on 2007-05-06
Hello, I am a new GNU/Linux user who is having trouble connecting to my wireless network in Ubuntu Feisty. Please answer my question that I posted at the end of [http://www.linuxquestions.org/questions/showthread.php?p=2737732#post2737732](http://www.linuxquestions.org/questions/showthread.php?p=2737732#post2737732)

---

### Post by l951b951 on 2007-05-06
I'm willing to try to help, but please post the question here.  That way if a solution is found, it will be available for other users to search the forums.  
That being said, have you searched the forums for your specific error message?

---

### Post by dylan623 on 2007-05-06
Actually, no, I did not search THESE forums.

The question:

For some reason, even though I installed ndiswrapper and the driver, I still can't get connected. The graphical tool I download from Synaptic says that the hardware is not present. Do I have the wrong driver? AFAIK I have the right one. Can anyone help?

Edit: lspci output:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

---

### Post by l951b951 on 2007-05-09
Have you tried [http://ubuntuforums.org/showthread.php?t=424994&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=424994&highlight=BCM4318) ?

---

### Post by dylan623 on 2007-05-09
No, but I looked at similar thread, I was planning to buy a new wireless card, but after seeing this, I might try again.

---

