---
title: "How can I use my internal modem ?"
date: 2018-12-05
forum: Apple Hardware Users
---

### Post by ff2008 on 2018-12-05
Dear all ,

I installed Ubuntu 16.04 Server in my iBook G4, but I can not use minicom to communicate with the internal modem.

I post some information that may be useful to describe the situation ---

[COLOR=#0BD100][FONT=Menlo][COLOR=#34bc26][    3.272098] [/COLOR][COLOR=#afad24]Serial[/COLOR]: 8250/16550 driver, 32 ports, IRQ sharing enabled[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo][COLOR=#34bc26][    3.281361] [/COLOR][COLOR=#afad24]pmac_zilog[/COLOR]: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo][COLOR=#34bc26][    3.282018] [/COLOR]Generic non-volatile memory driver v1.1[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo][COLOR=#34bc26][    3.282392] [/COLOR]Linux agpgart interface v0.103[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo][COLOR=#34bc26][    3.292071] [/COLOR][COLOR=#afad24]loop[/COLOR]: module loaded[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo][COLOR=#34bc26][    3.292802] [/COLOR]MacIO PCI driver attached to Intrepid chipset[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo][COLOR=#34bc26][    3.295271] [/COLOR][COLOR=#afad24]0.00013020:ch-a[/COLOR]: ttyPZ0 at MMIO 0x80013020 (irq = 22, base_baud = 230400) is a Z85c30 ESCC - Serial port[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo][COLOR=#34bc26][    3.296006] [/COLOR][COLOR=#afad24]0.00013000:ch-b[/COLOR]: ttyPZ1 at MMIO 0x80013000 (irq = 23, base_baud = 230400) is a Z85c30 ESCC - Serial port[/FONT][/COLOR]


[COLOR=#0BD100][FONT=Menlo]:~$ lspci -vvvv[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:0b.0 Host bridge: Apple Inc. UniNorth 2 PCI[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16, Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel modules: uninorth_agp[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Subsystem: Apple Inc. AirPort Extreme[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin A routed to IRQ 52[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at 80084000 (32-bit, non-prefetchable) [size=8K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: b43-pci-bridge[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel modules: ssb[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Intrepid Mac I/O[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16, Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at 80000000 (32-bit, non-prefetchable) [size=512K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: macio[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:18.0 USB controller: Apple Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin A routed to IRQ 27[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at <unassigned> (32-bit, non-prefetchable) [disabled] [size=4K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:19.0 USB controller: Apple Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin A routed to IRQ 28[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at <unassigned> (32-bit, non-prefetchable) [disabled] [size=4K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:1a.0 USB controller: Apple Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16 (750ns min, 21500ns max), Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin A routed to IRQ 29[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at 80083000 (32-bit, non-prefetchable) [size=4K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: ohci-pci[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:1b.0 USB controller: NEC Corporation OHCI USB Controller (rev 43) (prog-if 10 [OHCI])[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Subsystem: NEC Corporation USB Controller[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16 (250ns min, 10500ns max), Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin A routed to IRQ 63[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at 80082000 (32-bit, non-prefetchable) [size=4K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: ohci-pci[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:1b.1 USB controller: NEC Corporation OHCI USB Controller (rev 43) (prog-if 10 [OHCI])[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Subsystem: NEC Corporation USB Controller[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16 (250ns min, 10500ns max), Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin B routed to IRQ 63[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at 80081000 (32-bit, non-prefetchable) [size=4K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: ohci-pci[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0000:10:1b.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 04) (prog-if 20 [EHCI])[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Subsystem: NEC Corporation uPD72010x USB 2.0 Controller[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16 (4000ns min, 8500ns max), Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin C routed to IRQ 63[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at 80080000 (32-bit, non-prefetchable) [size=256][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: ehci-pci[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0001:20:0b.0 Host bridge: Apple Inc. UniNorth 2 Internal PCI[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16, Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel modules: uninorth_agp[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0001:20:0d.0 Unassigned class [ff00]: Apple Inc. UniNorth/Intrepid ATA/100[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 32, Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin ? routed to IRQ 39[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at f5004000 (32-bit, non-prefetchable) [size=16K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: pata-pci-macio[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0001:20:0e.0 FireWire (IEEE 1394): Apple Inc. UniNorth 2 FireWire (rev 81) (prog-if 10 [OHCI])[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Subsystem: Apple Inc. iBook G4 2004[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin A routed to IRQ 40[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at f5000000 (32-bit, non-prefetchable) [size=4K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: firewire_ohci[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel modules: firewire_ohci[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]0001:20:0f.0 Ethernet controller: Apple Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16 (16000ns min, 16000ns max), Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin A routed to IRQ 41[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at f5200000 (32-bit, non-prefetchable) [size=2M][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Expansion ROM at f5100000 [disabled] [size=1M][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: gem[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel modules: sungem[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]7f08:00:0b.0 Host bridge: Apple Inc. UniNorth 2 AGP[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 16, Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: agpgart-uninorth[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel modules: uninorth_agp[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]7f08:00:10.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV280/M9+ [Mobility Radeon 9200 AGP] (rev 01) (prog-if 00 [VGA controller])[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Apple iBook G4 2004[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Latency: 255 (2000ns min), Cache Line Size: 32 bytes[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Interrupt: pin A routed to IRQ 48[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 0: Memory at 98000000 (32-bit, prefetchable) [size=128M][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 1: I/O ports at 0400 [size=256][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Region 2: Memory at 90000000 (32-bit, non-prefetchable) [size=64K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Expansion ROM at 90020000 [disabled] [size=128K][/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel driver in use: radeon[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]	Kernel modules: radeonfb, radeon[/FONT][/COLOR]
[COLOR=#0BD100][FONT=Menlo]
[/FONT][/COLOR]

---

### Post by ff2008 on 2018-12-05
I doubt the pmac_zilog driver is not installed correctly :-(

Right should be some thing like the following (I googled on redhat dot com) ---


Apr 13 09:16:58 plantain kernel: pmac_zilog: 0.6 (Benjamin Herrenschmidt
<[EMAIL="benh@kernel.crashing.org"]benh@kernel.crashing.org[/EMAIL]>)
Apr 13 09:16:58 plantain kernel: pmac_zilog: i2c-modem detected, id: 1
Apr 13 09:16:58 plantain kernel: ttyPZ0 at MMIO 0x80013020 (irq = 22) is a
Z85c30 ESCC - Internal modem
Apr 13 09:16:58 plantain kernel: ttyPZ1 at MMIO 0x80013000 (irq = 50) is a
Z85c30 ESCC - Serial port

==> The pmac_zlog ports are named ttyPZ0 and ttyPZ1.

reconfigure minicom to use ttyPZ0:
* the modem now responds
* kernel module is used while minicom is running:

    pmac_zilog             22300  2

---

