---
title: "how do i tell how much VRAM my gpu has?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by 005david on 2007-11-01
it's intigrated, if that matters...
it's an "s3 unicrome"

if that would matter.

---

### Post by meatpan on 2007-11-01
One solution is to try running ```
lspci -vv
``` and looking for the gpu entry.  The vram info was present in my output, but I don't think there is any guarantee it will be there.

---

### Post by Hospadar on 2007-11-01
If you are using an nvidia card with the nvidia drivers you can get this info with nvidia-settings.  type "nvidia-settings" in the terminal

oops, your not. 

Well, if its an integrated card, it may well just share system memory.  I don't know of that many integrated graphics chipsets that have their own memory.
You may want to look instead into how much memory is allowed to be used by the video hardware (I have no idea how to do that personally though) or if there is a set amount that you can change (If thats what you want to do)  maybe try looking around in the bios.

---

### Post by 005david on 2007-11-01
> 00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
        Subsystem: VIA Technologies, Inc. P4M800 Host Bridge
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 8
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: f4000000-f7ffffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR+ <PERR+
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin B routed to IRQ 16
        Region 0: I/O ports at e100 [size=8]
        Region 1: I/O ports at e700 [size=4]
        Region 2: I/O ports at e800 [size=8]
        Region 3: I/O ports at e900 [size=4]
        Region 4: I/O ports at e000 [size=16]
        Region 5: I/O ports at d000 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 16
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        Region 4: I/O ports at e200 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 4: I/O ports at e300 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 4: I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 17
        Region 4: I/O ports at e500 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 17
        Region 4: I/O ports at e600 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 128 bytes
        Interrupt: pin C routed to IRQ 17
        Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: EPoX Computer Co., Ltd. Unknown device 3005
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 19
        Region 0: I/O ports at d400 [size=256]
        Capabilities: <access denied>

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
        Subsystem: EPoX Computer Co., Ltd. Unknown device 0c04
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 19
        Region 0: I/O ports at d800 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (750ns min, 2000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at dc00 [size=256]
        Region 1: Memory at fa001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA])
        Subsystem: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min)
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Region 1: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at f9000000 [disabled] [size=64K]
        Capabilities: <access denied>






uhh...

---

