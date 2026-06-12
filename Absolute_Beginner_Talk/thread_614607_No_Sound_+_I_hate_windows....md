---
title: "No Sound + I hate windows..."
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by DanielPeace... on 2007-11-16
I have recently installed Ubuntu and as well as being completely baffled by it, I'm also very impressed with it.

I installed Ubuntu after my copy of windows would no longer boot properly - BLUE SCREEN OF DEATH etc...

I had to run my PC in safe mode for a week before I got so insane that I decided to throw myself into the LInux world.

I still cant get the sound to work and wonder if it was anything related to me using my comp in safe mode. Can you recommend anything?

I've been through the complete sound guide but it doesnt really answer any of my questions. Sorry if i've repeated other people but im SOOOOOOO FRUSTRATED!

---

### Post by bluenova on 2007-11-16
What is your sound card and what version of Ubuntu are you running?

---

### Post by philinux on 2007-11-16
open a terminal and post the output of 

```
[FONT="Times New Roman"]lspci[/FONT]
```

---

### Post by apparle on 2007-11-16
I am also a beginner in linux and ubuntu.
i had a lot of problems starting sound on my pc.
I tried everything with alsa in vain.
At last I tried opensound drivers
[http://www.4front-tech.com/release/oss-linux_v4.0-1009_i386.deb](http://www.4front-tech.com/release/oss-linux_v4.0-1009_i386.deb)
See if these work.
Also see if you can get any help on IRC chat on irc.freenode.net

---

### Post by DanielPeace... on 2007-11-16
> **philinux said:**
> open a terminal and post the output of 

```
[FONT="Times New Roman"]lspci[/FONT]
```


im so so so sorry for this next question....really sorry....how do i get that symbol that is at the start of the code.

Also...apparle...i tried to install that programme and was met with the following..


"cannot continue"

argh!!!!

---

### Post by Joakim Stokland on 2007-11-16
That code is spelled LSPCI, only lower case. :)

---

### Post by Can+~ on 2007-11-16
Ok, even easier:

[LIST=1]
[*]Copy this command.
> lspci -vv > ~/Desktop/infopc
[*]Hit Alt+F2 and paste it there, Enter.
[*]Check your desktop, a file called "infopc" should appear on it.
[*]Copy the content and paste it here.
[/LIST]

---

### Post by monte48lowes on 2007-11-16
Daniel,

What computer are you running ubuntu on? I have a laptop I bought a couple of weeks ago for a great price $348. I got the blue screen after performing a windows update. I also has some issues with sound.

Open a terminal:

Applications > Accesories > Terminal

and enter the code below (you can copy from here and paste into the terminal)

```
lspci
```

Then copy the output of the terminal and paste in a reply window here.

Mike

---

### Post by DanielPeace... on 2007-11-16
Can + here is the code, it's quite lengthy!

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-d80fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c7ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at d8400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d4000000-d5ffffff
	Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d0000000-d1ffffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000c9ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000ce000000-00000000cfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=07, subordinate=08, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d2000000-d3ffffff
	Prefetchable memory behind bridge: 00000000ca000000-00000000cbffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 22
	Region 4: I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at d8404000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=09, subordinate=11, sec-latency=32
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d8100000-d81fffff
	Prefetchable memory behind bridge: 0000000050000000-0000000057ffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 18b0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 10
	Region 4: I/O ports at 18c0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300] (prog-if 00 [VGA])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at c0000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 2000 [size=256]
	Region 2: Memory at d8000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d8020000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d4000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1001
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

09:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at d8101000 (32-bit, non-prefetchable) [size=4K]
	Region 1: Memory at d8100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

09:04.1 CardBus bridge: O2 Micro, Inc. Unknown device 7175 (rev 21)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at d8108000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 00007000-000070ff
	I/O window 1: 00007400-000074ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

09:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at d8103000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at d8102000 (32-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: <access denied>

09:05.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at d8109000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=09, secondary=0e, subordinate=11, sec-latency=176
	Memory window 0: 54000000-57fff000 (prefetchable)
	Memory window 1: 5c000000-5ffff000
	I/O window 0: 00007800-000078ff
	I/O window 1: 00007c00-00007cff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

09:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 010d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max)
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at d8100800 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at d8104000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by DanielPeace... on 2007-11-16
Monte ...

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
09:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:04.1 CardBus bridge: O2 Micro, Inc. Unknown device 7175 (rev 21)
09:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
09:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
09:05.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by Martje_001 on 2007-11-16
You should read this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by monte48lowes on 2007-11-16
Daniel,

Martje has the right idea. I would also search the forums here for 'Acer', 'Intel Audio' and 'ALSA'.

Mike

---

### Post by stchman on 2007-11-16
I have a script that will update your ALSA driver.  It is for the ICH7 Intel HDA audio.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

It worked on my girlfriends laptop.  It uses the 1.0.14 alsa drivers, I am going to update it to use the 1.0.15 drivers.

---

### Post by Six Ways on 2007-11-16
I have a similar problem; I've been trying to get ubuntu to recognise my sound card for about a month and a half now with absolutely no success. The wierd thing is lspci lists the card properly, but nothing else on the system recognises the card. Even the proprietary driver installer says it can't find a supported card on my machine.

My specs are:
Asus P5N32 SLi Premium mobo
Soundblaster X-Fi MusicXtreme soundcard
Geforce 8800 GTX gpu
2gb ram

Any help appreciated. I've posted this a number of times but no luck so far.

---

### Post by stchman on 2007-11-19
> **Six Ways said:**
> I have a similar problem; I've been trying to get ubuntu to recognise my sound card for about a month and a half now with absolutely no success. The wierd thing is lspci lists the card properly, but nothing else on the system recognises the card. Even the proprietary driver installer says it can't find a supported card on my machine.

My specs are:
Asus P5N32 SLi Premium mobo
Soundblaster X-Fi MusicXtreme soundcard
Geforce 8800 GTX gpu
2gb ram

Any help appreciated. I've posted this a number of times but no luck so far.

Ubuntu and ALSA do not officially support the X-fi sound cards.  Creative has a beta X-fi driver on its site for Linux.

The best thing to do is email Creative and tell them that you will NEVER buy anymore of their products until they fully support Linux.  If enough folks do that then Creative will make an effort to support Linux.

---

### Post by apparle on 2008-02-12
I currently use OSS drivers.
No system sounds.
But OSS have beta for your card 
[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

---

