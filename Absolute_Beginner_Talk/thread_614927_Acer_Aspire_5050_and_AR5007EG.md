---
title: "Acer Aspire 5050 and AR5007EG"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by dskid807 on 2007-11-16
I installed ubuntu earlier and have 1 problem. My Atheros AR5007EG card won't install. I have followed the guides and end up with iwconfig saying it is a AR5006EG. Has anyone got any working drivers that won't be identified as an AR5006EG? I am currently using a broadcom pcmia card but that is limited to 11MB/s by the kernel drivers.

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"CLUBINTERNET-3B7EBD"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:19:15:3B:7E:C8   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level=-44 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:55  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
And lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

---

### Post by overdrank on 2007-11-16
HI and this thread helped me and it has helped some uses in 7.10 Gutsy.
[http://ubuntuforums.org/showthread.php?t=512828&highlight=AR5007EG](http://ubuntuforums.org/showthread.php?t=512828&highlight=AR5007EG)
In my acer ubuntu said it was a 5006 and vista said 5007 and I followed that " how to " in feisty and it worked. Good luck!

---

