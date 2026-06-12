---
title: "What graphics-card do i have??"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-11-15
Hello folks,
I have an acer aspire 5004 laptop, and i use Ubuntu-dapper. The machine has a crappy Sis chipset, with shared video memory. I wanted to know whether i will be able to make any use of the graphics-card- but i dont know the model number. 
Here is the lspci output:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
----------------------------------------------
However, xorg.conf says this:

  BoardName    "SiS 660"
  BusID        "1:0:0"
  Driver       "sis"
  Identifier   "Device[0]"
  Screen       0
  VendorName   "SiS"
---------------------------------------------
After some researching, i have found out that there is no DRI for SIS 760- but is 760 my card, or is it 660, or maybe something else? Which driver do i need to install??
Thanks..

---

### Post by steven8 on 2006-11-15
Here is a rather interesting article about your very situation:

[http://en.linux.wikia.com/wiki/Acer_aspire_5004]("http://en.linux.wikia.com/wiki/Acer_aspire_5004")

---

### Post by kitt on 2006-11-15
Thanks, steven. 
I am a bit confused about 'chipset' and graphics-card..since i have onboard graphics.

---

### Post by steven8 on 2006-11-15
> Chipset
From Wikipedia, the free encyclopedia
Jump to: navigation, search

A chipset is a group of integrated circuits ("chips") that are designed to work together, and are usually marketed as a single product. In computing, the term chipset is commonly used to refer to the specialized motherboard chips on a computer or expansion card. When discussing personal computers (PCs) based on recent Intel Pentium-class systems, the term "chipset" often refers to the two main motherboard chips: northbridge and southbridge. The manufacturer of a chipset often is independent from the manufacturer of the motherboard. Examples of manufactors of PC motherboard chipsets include NVIDIA, ATI, VIA Technologies, SiS and Intel. [1] [2] [3] [4] [5] [6]

In home computers, game consoles and arcade game hardware of the 1980s and 1990s, the term chipset was used for the custom audio and graphics chips. Examples include the Commodore Amiga's Original Chip Set or SEGA's System 16 chipset.

Computer systems produced since the late 1980s share commonly used chipsets, even across widely disparate computing specialties. For example, the NCR 53C9x, a low-cost chipset implementing a SCSI interface to storage devices, could be found in Unix machines (such as the MIPS Magnum), embedded devices and personal computers

SIS Chipsets:
 
[http://www.sis.com/products/product_000001.htm]("http://www.sis.com/products/product_000001.htm")

---

