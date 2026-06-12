---
title: "trouble detecting wireless with corega"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-07-08
For some reason, I've been having problems with having wireless connections with Ubuntu. I'm using a Corega wireless USB stick and just can't figure out how to get it detected with Linux. I did a googling around but no success with finding a solution to my problem.

   I'm using a Corega USB model  CG-WLUSB2GS. 

 All help is greatly appreciated!

---

### Post by orb9220 on 2007-07-08
run a term and enter: **lspci**

and post results here

---

### Post by crazydiver on 2007-07-10
thanks man!

---

### Post by crazydiver on 2007-07-10
here are the results... sorry its late... I have problems commuting to a comp connected online


00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910 
00:02.0 PCI bridge: ATI Technologies Inc Unknown device 7913 
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7917 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 13) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0421 (rev a1) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01) 
03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

---

### Post by orb9220 on 2007-07-10
Sorry but after googling it I find that getting it to work would most likely in the realm of Tachyon Particles. Theoretically possible but unlikely.

---

