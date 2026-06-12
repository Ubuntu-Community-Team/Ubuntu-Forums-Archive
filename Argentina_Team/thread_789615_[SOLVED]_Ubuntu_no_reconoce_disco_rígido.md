---
title: "[SOLVED] Ubuntu no reconoce disco rígido"
date: 2008-05-10
forum: Argentina Team
---

### Post by gaboherno on 2008-05-10
Hola qué tal?
Tengo problemas para instalar Ubuntu versión 6.06 LTS para PC's de 64 bits desde el live CD.
No me detecta el disco rígido, se queda en el paso de particionar (no se cuelga, pero tampoco avanza).
Cuando le doy fdisk /dev/hda desde la terminal, me parece que toma el CD en vez de tomar el disco rígido.
Para colmo, tengo un GNU/Linux Debian más antiguo que sí detecta el disco rígido y se instala bien.
A continuación voy a dejar algunos datos de mi PC, observar que lshw no detecta que hay un disco rígido (al menos eso me parece):

********** Algunos dispositivos detectados por la BIOS **********
1:
ATA(PI) Device(s): Third Master
Type: Hard disk
Size: 120 GB
LBA Mode: LBA
Block Mode: 16 sec
Smart Info: good
32bit Mode: on
DMA Mode: UDMA6
PIO Mode: 4

2:
ATA(PI) Device(s): Primary Master
Type: ATAPI CD-ROM
DMA Mode: UDMA2
PIO Mode: 4

********** lspci -vv **********

0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
	Subsystem: ATI Technologies Inc RS480 Host Bridge
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
00: 02 10 50 59 06 00 20 22 10 00 00 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 02 10 50 59
30: 00 00 00 00 c4 00 00 00 00 00 00 00 00 00 00 00

0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: ff400000-ff4fffff
	Prefetchable memory behind bridge: 00000000cff00000-00000000dfe00000
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [44] #08 [a803]
	Capabilities: [b0] #0d [0000]
00: 02 10 3f 5a 07 01 30 02 00 00 04 06 00 40 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 40 a1 a1 20 02
20: 40 ff 40 ff f1 cf e1 df 00 00 00 00 00 00 00 00
30: 00 00 00 00 44 00 00 00 00 00 00 00 00 00 0a 00

0000:00:12.0 IDE interface: ATI Technologies Inc: Unknown device 4380 (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at e800 [size=8]
	Region 1: I/O ports at e400 [size=4]
	Region 2: I/O ports at e000 [size=8]
	Region 3: I/O ports at dc00 [size=4]
	Region 4: I/O ports at d800 [size=16]
	Region 5: Memory at ff6ffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] #12 [0010]
00: 02 10 80 43 07 01 30 02 00 8f 01 01 10 40 00 00
10: 01 e8 00 00 01 e4 00 00 01 e0 00 00 01 dc 00 00
20: 01 d8 00 00 00 fc 6f ff 00 00 00 00 62 14 42 72
30: 00 00 00 00 60 00 00 00 00 00 00 00 0b 01 00 00

0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4387 (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin A routed to IRQ 177
	Region 0: Memory at ff6fe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
00: 02 10 87 43 17 01 b0 02 00 10 03 0c 10 40 80 00
10: 00 e0 6f ff 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 d0 00 00 00 00 00 00 00 0a 01 00 00

0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4388 (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin B routed to IRQ 185
	Region 0: Memory at ff6fd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
00: 02 10 88 43 17 01 b0 02 00 10 03 0c 10 40 00 00
10: 00 d0 6f ff 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 d0 00 00 00 00 00 00 00 0a 02 00 00

0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4389 (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin C routed to IRQ 193
	Region 0: Memory at ff6fc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
00: 02 10 89 43 17 01 b0 02 00 10 03 0c 10 40 00 00
10: 00 c0 6f ff 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 d0 00 00 00 00 00 00 00 05 03 00 00

0000:00:13.3 USB Controller: ATI Technologies Inc: Unknown device 438a (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin B routed to IRQ 185
	Region 0: Memory at ff6fb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
00: 02 10 8a 43 17 01 b0 02 00 10 03 0c 10 40 00 00
10: 00 b0 6f ff 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 d0 00 00 00 00 00 00 00 0a 02 00 00

0000:00:13.4 USB Controller: ATI Technologies Inc: Unknown device 438b (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin C routed to IRQ 193
	Region 0: Memory at ff6fa000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
00: 02 10 8b 43 17 01 b0 02 00 10 03 0c 10 40 00 00
10: 00 a0 6f ff 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 d0 00 00 00 00 00 00 00 05 03 00 00

0000:00:13.5 USB Controller: ATI Technologies Inc: Unknown device 4386 (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin D routed to IRQ 201
	Region 0: Memory at ff6ff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [e4] #0a [20e0]
00: 02 10 86 43 17 01 b0 02 00 20 03 0c 10 40 00 00
10: 00 f8 6f ff 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 c0 00 00 00 00 00 00 00 05 04 00 00

0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4385 (rev 13)
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Region 0: I/O ports at 0b00 [size=16]
	Region 1: Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [b0] #08 [a802]
00: 02 10 85 43 03 04 30 02 13 00 05 0c 00 00 80 00
10: 01 0b 00 00 00 00 d0 fe 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 b0 00 00 00 00 00 00 00 00 00 00 00

0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 438c (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 0
	Region 0: I/O ports at <unassigned>
	Region 1: I/O ports at <unassigned>
	Region 2: I/O ports at <unassigned>
	Region 3: I/O ports at <unassigned>
	Region 4: I/O ports at ff00 [size=16]
	Capabilities: [70] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
00: 02 10 8c 43 05 00 30 02 00 8a 01 01 00 00 00 00
10: 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00
20: 01 ff 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 70 00 00 00 00 00 00 00 00 01 00 00

0000:00:14.2 0403: ATI Technologies Inc: Unknown device 4383
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin A routed to IRQ 15
	Region 0: Memory at ff6f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
00: 02 10 83 43 06 00 10 04 00 00 03 04 10 40 00 00
10: 04 40 6f ff 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 50 00 00 00 00 00 00 00 0f 01 00 00

0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 438d
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
00: 02 10 8d 43 0f 00 20 02 00 00 01 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4384 (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ff500000-ff5fffff
	Prefetchable memory behind bridge: 40000000-400fffff
	BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
00: 02 10 84 43 07 01 a0 02 00 01 04 06 00 40 81 00
10: 00 00 00 00 00 00 00 00 00 02 02 40 b0 b0 80 22
20: 50 ff 50 ff 00 40 00 40 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 03 00

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: [80] #08 [2101]
00: 22 10 00 11 00 00 10 00 00 00 00 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 80 00 00 00 00 00 00 00 00 00 00 00

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
00: 22 10 01 11 00 00 00 00 00 00 00 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
00: 22 10 02 11 00 00 00 00 00 00 00 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: [f0] #0f [0010]
00: 22 10 03 11 00 00 10 00 00 00 00 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 f0 00 00 00 00 00 00 00 00 00 00 00

0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5974 (prog-if 00 [VGA])
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 7242
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (2000ns min), Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at a800 [size=256]
	Region 2: Memory at ff4f0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at ff4c0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
00: 02 10 74 59 07 01 b0 02 00 00 00 03 10 40 00 00
10: 08 00 00 d0 01 a8 00 00 00 00 4f ff 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 42 72
30: 00 00 4c ff 50 00 00 00 00 00 00 00 0a 01 08 00

0000:02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8167 (rev 10)
	Subsystem: Micro-Star International Co., Ltd.: Unknown device 242c
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin A routed to IRQ 209
	Region 0: I/O ports at b800 [size=256]
	Region 1: Memory at ff5ffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 40000000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
00: ec 10 67 81 07 00 b0 02 10 00 00 02 10 40 00 00
10: 01 b8 00 00 00 fc 5f ff 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 2c 24
30: 00 00 5c ff dc 00 00 00 00 00 00 00 09 01 20 40

********** lsmod **********

Module                  Size  Used by
nls_utf8                3584  1 
vfat                   16768  1 
fat                    57136  1 vfat
sg                     43568  0 
sd_mod                 21504  1 
usb_storage            81984  1 
scsi_mod              160504  3 sg,sd_mod,usb_storage
ipv6                  300416  10 
rfcomm                 45600  0 
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0 
lp                     15040  0 
radeon                124320  0 
drm                    96296  1 radeon
cpufreq_userspace       9184  0 
cpufreq_stats           8264  0 
freq_table              6464  1 cpufreq_stats
cpufreq_powersave       3328  0 
cpufreq_ondemand        9768  0 
cpufreq_conservative    10984  0 
video                  18824  0 
tc1100_wmi              9096  0 
sony_acpi               7188  0 
pcc_acpi               16128  0 
hotkey                 13768  0 
dev_acpi               15364  0 
container               6272  0 
button                  8864  0 
acpi_sbs               24600  0 
battery                12296  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
i2c_core               26624  1 i2c_acpi_ec
ac                      7176  1 acpi_sbs
dm_mod                 63176  0 
af_packet              28172  2 
md_mod                 76792  0 
tsdev                  10240  0 
floppy                 74120  0 
shpchp                 51360  0 
psmouse                40452  0 
parport_pc             40944  1 
parport                44172  3 ppdev,lp,parport_pc
r1000                  19328  0 
pcspkr                  3592  0 
serio_raw               9732  0 
pci_hotplug            33168  1 shpchp
evdev                  14464  1 
squashfs               44416  1 
unionfs                94232  1 
loop                   19216  2 
nls_cp437               8320  2 
isofs                  39808  1 
ide_cd                 35744  1 
cdrom                  41144  1 ide_cd
ide_generic             2816  0 
ehci_hcd               34568  0 
ohci_hcd               23684  0 
usbcore               145980  4 usb_storage,ehci_hcd,ohci_hcd
generic                 7300  0 
thermal                16524  0 
processor              29224  1 thermal
fan                     6408  0 
capability              7176  0 
commoncap               9728  1 capability
vesafb                 10920  1 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4224  1 vesafb
cfbfillrect             5760  1 vesafb
fbcon                  43136  72 
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit

********** lshw **********

ubuntu
    description: Desktop Computer
    product: MS-7242
    vendor: MSI
    version: 0A
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: MS-7242
       vendor: MSI
       physical id: 1
       version: 0A
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080013 (07/04/2006)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KB
             capacity: 128KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM Synchronous 266 MHz (3.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
             clock: 266MHz (3.7594ns)
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM Synchronous 266 MHz (3.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 512MB
             width: 64 bits
             clock: 266MHz (3.7594ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                logical name: /dev/fb0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list fb
                configuration: depth=24 frequency=75.69Hz mode=1024x768 visual=truecolor xres=1024 yres=768
                resources: iomemory:d0000000-d7ffffff ioport:a800-a8ff iomemory:ff4f0000-ff4fffff irq:10
        *-ide:0 UNCLAIMED
             description: IDE interface
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             resources: ioport:e800-e807 ioport:e400-e403 ioport:e000-e007 ioport:dc00-dc03 ioport:d800-d80f iomemory:ff6ffc00-ff6fffff irq:11
        *-usb:0
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:ff6fe000-ff6fefff irq:177
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-amd64-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Interfase MIDI - USB NNV
                   vendor: NNV
                   physical id: 1
                   bus info: usb@1:1
                   version: 4.00
                   serial: 12345678
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:ff6fd000-ff6fdfff irq:185
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-amd64-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:ff6fc000-ff6fcfff irq:193
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-amd64-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:ff6fb000-ff6fbfff irq:185
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-amd64-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:ff6fa000-ff6fafff irq:193
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-amd64-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ff6ff800-ff6ff8ff irq:201
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-23-amd64-generic ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s
              *-usb:0 UNCLAIMED
                   description: Generic USB device
                   product: USB WLAN Device
                   vendor: Atheros Communications Inc
                   physical id: 4
                   bus info: usb@6:4
                   version: 0.01
                   serial: 1.0
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
              *-usb:1
                   description: Mass storage device
                   product: USB 2.0(HS) Flash Disk
                   vendor: Actions Semiconductor Co., Ltd
                   physical id: 6
                   bus info: usb@6:6
                   logical name: scsi0
                   version: 1.00
                   serial: A00000600001
                   capabilities: usb-2.00 emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      vendor: USB 2.0
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      size: 3914MB
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                         size: 3914MB
        *-serial UNCLAIMED
             description: SMBus
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             resources: ioport:b00-b0f iomemory:fed00000-fed003ff
        *-ide:1 UNCLAIMED
             description: IDE interface
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             resources: ioport:ff00-ff0f
        *-multimedia UNCLAIMED
             description: Multimedia controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:ff6f4000-ff6f7fff irq:15
        *-isa UNCLAIMED
             description: ISA bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Ethernet interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@02:06.0
                logical name: eth0
                version: 10
                serial: 00:19:db:2e:07:6f
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r1000 multicast=yes
                resources: ioport:b800-b8ff iomemory:ff5ffc00-ff5ffcff irq:209
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
  *-ide
       description: IDE Channel 0
       physical id: 0
       bus info: ide@0
       logical name: ide0
     *-cdrom
          description: DVD-RAM writer
          product: HL-DT-STDVD-RAM GSA-H20N
          physical id: 0
          bus info: ide@0.0
          logical name: /dev/hda
          version: 1.01
          capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: mode=udma2
        *-disc
             physical id: 0
             logical name: /dev/hda

********** mount -l **********

unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-amd64-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8)

********** df **********

df -k /
Filesystem           1K-blocks      Used Available Use% Mounted on
unionfs                1088532    688804    399728  64% /

df -k /cdrom
Filesystem           1K-blocks      Used Available Use% Mounted on
-                       715670    715670         0 100% /cdrom

df -k /media/usbdisk
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda               4000960   3979888     21072 100% /media/usbdisk

df -k /dev/hda
Filesystem           1K-blocks      Used Available Use% Mounted on
udev                    449492        80    449412   1% /dev

********************
¿Qué puedo hacer?
Les mando un saludo grande, hasta luego.

---

### Post by Mauro22 on 2008-05-10
Ubuntu 6.06?


Porque no probas con la ultima y en la version de 32 bits. Los 64 bits dan muchos problemas!

---

### Post by gaboherno on 2008-05-12
Gracias Mauro22, ya estuve mirando un poco lo que se habla en este lugar sobre 32 vs. 64, y ver que tiene algunos problemas el de 64.

[http://ubuntuforums.org/showthread.php?t=788821](http://ubuntuforums.org/showthread.php?t=788821)

Saludos,
gaboherno


PD.: El problema que tenía lo pude solucionar cambiando el "Live CD" por el "Alternate CD", se instaló y arrancó. Sin embargo, después de loguearme la pantalla se pone negra y vuelve a la pantalla de login, siempre vuelve a la pantalla de login, nunca entra al escritorio, y tampoco se puede cambiar a otra terminal. Pero esto ya lo voy a preguntar en un nuevo hilo. Gracias ! ! !

---

### Post by guillermolisi on 2008-05-13
Cuando hagas la consulta no olvides de poner el modelo de tu placa de video.

Hay cantidad de mensajes que hablan sobre problemas de video como el que mencionas, en este foro como en otros en Ingles.

---

