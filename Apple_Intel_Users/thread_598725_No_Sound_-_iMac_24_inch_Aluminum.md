---
title: "No Sound - iMac 24 inch Aluminum"
date: 2007-10-31
forum: Apple Intel Users
---

### Post by dgillett on 2007-10-31
First let me start off by saying I know this is has been asked and answered and for that I am sorry, but I can not seem to get the sound working at all in gutsy. 

Ok, so  I have the new 24 inch Aluminum iMac. I have tried most of the steps on the other posts but still nothing. 

Tried new alsa drivers, nothing. 
Tried posted solutions but still nothing. 

REALTEK ALC882
HDA Intel

Thanks for any help at all!

---

### Post by nicfagn on 2007-11-01
You have to post at least this info:

- lspci -vvnn
- cat /proc/asound/version
- cat /proc/asound/card0/codec#0
- amixer

---

### Post by dgillett on 2007-11-01
Here you go and thanks again!

**lspci -vvnn:**
> 
root@root-desktop:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0600000-d06fffff
        Prefetchable memory behind bridge:
00000000c0000000-00000000cfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 [8086:2834] (rev 03) (prog-if 00 [UHCI])
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 19
        Region 4: I/O ports at 40c0 [size=32]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) (prog-if 00 [UHCI])
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 16
        Region 4: I/O ports at 40a0 [size=32]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family)
USB2 EHCI Controller #2 [8086:283a] (rev 03) (prog-if 20 [EHCI])
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 21
        Region 0: Memory at d0704c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at d0700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: d0500000-d05fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: d0400000-d04fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: d0300000-d03fffff
        Prefetchable memory behind bridge:
00000000d0000000-00000000d00fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge:
00000000d0800000-00000000d08fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) (prog-if 00 [UHCI])
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 4: I/O ports at 4080 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) (prog-if 00 [UHCI])
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 20
        Region 4: I/O ports at 4060 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) (prog-if 00 [UHCI])
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 21
        Region 4: I/O ports at 4040 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family)
USB2 EHCI Controller #1 [8086:2836] (rev 03) (prog-if 20 [EHCI])
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 19
        Region 0: Memory at d0704800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        Memory behind bridge: d0100000-d01fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM
(ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at 40e0 [size=16]

00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM
(ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 20
        Region 0: I/O ports at 40f8 [size=8]
        Region 1: I/O ports at 4114 [size=4]
        Region 2: I/O ports at 40f0 [size=8]
        Region 3: I/O ports at 4110 [size=4]
        Region 4: I/O ports at 4020 [size=16]
        Region 5: I/O ports at 4000 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
        Subsystem: Apple Computer Inc. Unknown device [106b:00a0]
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 10
        Region 0: Memory at d0705000 (32-bit, non-prefetchable) [size=256]
        Region 4: I/O ports at efa0 [size=32]

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:9583] (prog-if 00 [VGA])
        Subsystem: Apple Computer Inc. Unknown device [106b:0083]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Region 2: Memory at d0620000 (64-bit, non-prefetchable) [size=64K]
        Region 4: I/O ports at 3000 [size=256]
        Expansion ROM at d0600000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 FireWire (IEEE 1394) [0c00]: Agere Systems Unknown device [11c1:5901] (rev 05) (prog-if 10 [OHCI])
        Subsystem: Agere Systems Unknown device [11c1:5900]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at d0400000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

04:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
        Subsystem: Apple Computer Inc. Unknown device [106b:0088]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at d0300000 (64-bit, non-prefetchable) [size=16K]
        Region 2: Memory at d0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>

05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd.
Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev
13)
        Subsystem: Marvell Technology Group Ltd. Unknown device [11ab:00ba]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-
ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at d0200000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at 2000 [size=256]
        Expansion ROM at d0800000 [disabled] [size=128K]
        Capabilities: <access denied>

**cat /proc/asound/version:**

> Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31
09:03:25 2007 UTC).

**cat /proc/asound/card0/codec#0:**

> root@root-desktop:~$ cat /proc/asound/card0/codec#0
Codec: Realtek ALC885
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3200
Revision Id: 0x100103
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x00 0x00] [0x00 0x00] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x90100140: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x012b4050: [Jack] HP Out at Ext Rear
    Conn = Comb, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x083c: IN OUT HP Detect
  Pin Default 0x90100141: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x90a00110: [Fixed] Mic at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x24: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x018b3020: [Jack] Line In at Ext Rear
    Conn = Comb, Color = Blue
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x014be060: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = White
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x0820: IN
  Pin Default 0x01cbe030: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = White
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b Node 0x25 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x25 0x0b

**amixer:**


> root@root-desktop:~$ amixer
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [on]
  Front Right: Playback 0 [0%] [-64.00dB] [on] Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB] Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on] Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on] Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on] Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on] Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off] Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 0 [0%] [-30.00dB]
  Front Right: Capture 0 [0%] [-30.00dB] Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'

Thanks!

---

### Post by dgillett on 2007-11-01
Note: I also obtained this information from KinfoCenter

Audio Device:
0: ALC882 Analog (DUPLEX)

Mixer:
0:Realtek ALC885

Thanks again!

---

### Post by nicfagn on 2007-11-03
Download **alsa-driver-1.0.15** sources from:
 [INDENT][ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2")[/INDENT] 
Expand the sources with:
```
tar --bzip2 -xvf alsa-driver-1.0.15.tar.bz2
```

Install the libc6 developer libraries and the patch program,  if missing:

```
sudo apt-get install libc6-dev patch
```

Download the attached patch, copy it into **alsa-driver-1.0.15/alsa-kernel/pci/hda** and cd to that directory.
Apply the patch with:

```
patch < alsa-1.0.15-imac.txt
```

Cd back to the top **alsa-driver-1.0.15** dir and do a configure for the HDA intel chipset:
 
```
./configure --with-cards=hda-intel
```

Compile with the command:

```
make -j3
```

For **Gutsy** or later, a little adjustment is needed to use the compiled module instead of the one shipped with the system (in previous versions this command should fail):

```
sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
```

Install the compiled modules:

```
sudo make install-modules
```

Reboot and you should be able to hear sound from the speakears, but not from headphones and no mic either, at least according to reports from other users. 
Strangely, speakers automuting when you insert the headphones should work.
Since I don't have the specific model to do the testing, I can't do better, sorry.

Just a note: since the stable version of alsa-driver-1.0.15 is out, I did the patch based on that version, but the patch is functionally the same as the one I previously did for alsa-driver-1.0.14 in another thread.
There are some advantages though: power saving is enabled, consuming less energy when sound is idle, and, if suspension work on your system, sound will work after a resume.

---

### Post by cyberdork33 on 2007-11-03
Note, the install 'patch' step should be done before you actually use the patch utility ;)

---

### Post by nicfagn on 2007-11-03
> **cyberdork33 said:**
> Note, the install 'patch' step should be done before you actually use the patch utility ;)

Good catch, I didn't notice that. :)
I remembered that the compilation process needed to patch some files but I didn't see that it was needed anyway to apply my patch.

I edited the post accordingly, thanks.

---

### Post by dgillett on 2007-11-05
Awesome, it worked! :)

Thanks!

Now, I can hear sound on the internal speakers just fine.

On the Headphone jack I can hear sound but Very Very Quietly.

Thanks again!

---

### Post by nicfagn on 2007-11-05
:popcorn:

Good listening!

---

### Post by pizzapanther on 2007-12-04
Thanks for the patch it worked great!   Anyone get the headphone jack working though?

---

### Post by AlainJLEB on 2007-12-05
I followed that path as well, and now I have sound ... but the quality is not there: lot's of noise is present, not completely covering the sound, but it looks more like an old radio rather than a new iMac :(

Any suggestion on how to improve this?

---

### Post by cyberdork33 on 2007-12-05
> **AlainJLEB said:**
> I followed that path as well, and now I have sound ... but the quality is not there: lot's of noise is present, not completely covering the sound, but it looks more like an old radio rather than a new iMac :(

Any suggestion on how to improve this?

If you area getting static, try rebooting first, and if that doesn't work, then you might run alsamixer and try to turn one of the channels down slightly to get rid of the noise.

---

### Post by AlainJLEB on 2007-12-06
I have already rebooted to load the new module and this does not solve. There is sound coming out of the speaker, but there is so much noise that it is not very funny to listen :(

Regarding the channels, I only have Master and PCM ... and nothing more ... strange, when under alsa 1.0.14, I was having much more choice.

Any idea is welcome ... :)

---

### Post by AlainJLEB on 2007-12-06
I have recompiled alsa-1.0.15 **_without_** applying the patch, and the result is:
[LIST]
[*]no sound at all
[*]more channels available in alsamixer: Headphon, PCM, Front, Surround, Line, Mic & Mic Boos
[/LIST]

When using patched version, I only have Master and PCM, I can hear music, but it's "hidden" behind lots of static noise. Rebooting does not help ... is there a specific option to pass to the module to let it know it's an imac 2007?

---

### Post by cyberdork33 on 2007-12-06
> **AlainJLEB said:**
> I have recompiled alsa-1.0.15 **_without_** applying the patch, and the result is:[LIST]
[*]no sound at all
[*]more channels available in alsamixer: Headphon, PCM, Front, Surround, Line, Mic & Mic Boos[/LIST]
When using patched version, I only have Master and PCM, I can hear music, but it's "hidden" behind lots of static noise. Rebooting does not help ... is there a specific option to pass to the module to let it know it's an imac 2007?

the patch is specifically for your mac, so it may be a bug. I would guess you should have many more channels.

---

### Post by AlainJLEB on 2007-12-06
I have tried several other options, like setting "options snd-hda-intel model=imac", but this does not help at all.
```
cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC885
```

Any other suggestion?

---

### Post by Askrates on 2007-12-14
Bump.

I have the same problem with my aluminum iMac. 

Without the patch there is no sound at all.

With the path, there is discernible noise when playing any audio. And the microphone doesn't work.

---

### Post by yxvaan on 2007-12-20
I have been scanning through these iMac sound threads when trying to get something out of my own aluminium 24" iMac with a amd64 version Xubuntu 7.10 installed in it. Here's some further information just in case it gives some clues as to why the drivers and patches behave in my machine as they do:

 *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

Codec: Realtek ALC885
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3200
Revision Id: 0x100103

I have tried out both the alsa drivers and the patches nicfagn has been so diligently posting. So far, the most promising combination has been the [alsa-driver-1.0.14](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2) patched with [post=3519262]alsa-1.0.14-patch_realtek-imac24_v2-3.txt[/post]. With them, the sound comes out from both the internal loudspeakers and the headphones, which mute the loudspeakers just as they should. However, the headphone volume is very low: you hear hardly anything. With an amplifier and external loudspeakers you get an acceptable performance when the amplifier volume is turned to the max. Recording works both with an external microphone and the built-in one. Of the digital ins and outs I can't say anything as I haven't got the necessary equipment.

The results from the 1.0.1.14 driver patched with the alsa-1.0.14-patch...v2_4.txt and 1.0.1.15 driver and the alsa-1.0.15-imac.txt patch weren't as good. To start with, the patch command didn't like the alsa-1.0.14-patch...v2_4.txt:

ch_realtek-imac24_v2-4.txt 
patching file patch_realtek.c
patch unexpectedly ends in middle of line
Hunk #5 succeeded at 5590 with fuzz 1.

Anyhow, I compiled an installed the driver but the result wasn't any better than with a patchless driver: the sound came out from the front loudspeakers and nothing else. The patched 1.0.15 driver was a little better: the sound came out also from the headphones and the muting functioned but the volume was as weak as ever. Recording didn't function at all.

As a conclusion, it seems to me that the alsa-1.0.14-patch_realtek-imac24_v2-3.txt is the most promising. Would it be possible to still sort out the headspeaker volume problem? Then it would be perfect. Even though I'm already very thankfull of the present situation. It's much better than no sound at all.

---

### Post by antoniogartime on 2008-01-19
Hello everybody:

I tried all the patches in this forum and no one let me hear anything from speakers. The last one I tried (alsa-1015-imac.txt), give me this hunks:

> 
root@iUbuntu:/opt/alsa-driver-1.0.15/pci/hda# patch < alsa-1015-imac.txt 
patching file patch_realtek.c
Hunk #1 FAILED at 159.
Hunk #2 FAILED at 5314.
Hunk #3 FAILED at 5508.
Hunk #4 FAILED at 5652.
Hunk #5 FAILED at 5755.
Hunk #6 FAILED at 5986.
6 out of 6 hunks FAILED -- saving rejects to file patch_realtek.c.rej


My computer is a new Imac Aluminium 20', Intel Core 2 DUO with 2GB RAM and ATI HD 2400 XT. Everything works fine, excepts sound.

Here my "aplay -l":
> 
root@iUbuntu:/opt/alsa-driver-1.0.15/pci/hda# aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC882 Analog [ALC882 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC882 Digital [ALC882 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


I tried both alsa-1.0.14 as alsa-1.0.15. I would really appreciate your help. Many thanks!

--
**Antonio González Artime**

---

### Post by antoniogartime on 2008-01-19
> **antoniogartime said:**
> Hello everybody:

I tried all the patches in this forum and no one let me hear anything from speakers. The last one I tried (alsa-1015-imac.txt), give me this hunks:



My computer is a new Imac Aluminium 20', Intel Core 2 DUO with 2GB RAM and ATI HD 2400 XT. Everything works fine, excepts sound.

Here my "aplay -l":


I tried both alsa-1.0.14 as alsa-1.0.15. I would really appreciate your help. Many thanks!

--
**Antonio González Artime**

Sorry about this. My problem was (I think) that I was trying to apply patch in ../alsa-driver-1.0.15/pci/hda   and not in /alsa-driver-1.0.15/**alsa-kernel**/pci/hda

I'm going now to try it...

---

### Post by antoniogartime on 2008-01-19
It works perfectly! Thank you!

---

### Post by nicfagn on 2008-01-19
I'm happy it worked for you. :)

Ciao

---

### Post by diddledan on 2008-01-24
> **nicfagn said:**
> Reboot and you should be able to hear sound from the speakears, but not from headphones and no mic either, at least according to reports from other users. 
Strangely, speakers automuting when you insert the headphones should work.
Since I don't have the specific model to do the testing, I can't do better, sorry.


well this is the thing.. speakers are connected via the headphone socket, so if you can't hear anything with headphones, then you also can't hear anything through external speakers.

the only caveat to the above statement of mine, is if you are utilising the digital speaker connection? (also in the same socket as the headphones?)

---

### Post by nicfagn on 2008-01-24
> **diddledan said:**
> well this is the thing.. speakers are connected via the headphone socket, so if you can't hear anything with headphones, then you also can't hear anything through external speakers.
For speakers automuting, I mean how it works in Mac OS X: if I'm listening music with my Mac and I plug in the headphones, I can hear the sound only from headphones and not from the built-in speakers.

External speakers should behave just like headphones, as you said.

Bye

---

### Post by diddledan on 2008-01-24
aha, being a new mac user I didn't realise the internal speakers were useful for anything other than the startup chime :-/ I've now unplugged my external speakers and am happily using the internal ones. thankyou for the patch and support, nicfagn

---

### Post by jmplaza on 2008-02-12
I am quite sure that the SOLUTION is (Tested for Imac Intel Core 2 Duo 20" 2Ghz with Intel HDA 82801H (rev 03) Soundcard) the following with Ubuntu 7.10:

1. Uninstall the default Alsa (1.0.14)
apt-get remove alsa-base
2. Prerequisites for compiling (maybe g++ cpp or similar are also needed, depending on your installation)
apt-get install libc6-dev
3. Download the latest stable realease of alsa 1.0.16 (February 6th) from alsa project ftp
4. Compile:
./configure --with-cards=hda-intel
make -j3
mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
make install-modules

5. Add to /etc/modprobe.d/alsa-base
options snd-hda-intel model=mbp3 (as it was a mac book pro 3...)

and IT WORKS!!!! Hope it works for you too...
With alsa 1.0.16 there is no need to patch and model=3stack seems not to work as some people said with alsa 1.0.15
Regards,
Josema

---

### Post by diddledan on 2008-03-03
> **jmplaza said:**
> I am quite sure that the SOLUTION is (Tested for Imac Intel Core 2 Duo 20" 2Ghz with Intel HDA 82801H (rev 03) Soundcard) the following with Ubuntu 7.10:

5. Add to /etc/modprobe.d/alsa-base
options snd-hda-intel model=mbp3 (as it was a mac book pro 3...)


how can this be tested for an imac when the instructions are clearly for a macbook pro 3? what model should one enter to get things working on an aluminium imac 24inch 2007 machine?

(I'ma stick with nicfagn's patch)

---

### Post by cyberdork33 on 2008-03-03
> **diddledan said:**
> how can this be tested for an imac when the instructions are clearly for a macbook pro 3? what model should one enter to get things working on an aluminium imac 24inch 2007 machine?

(I'ma stick with nicfagn's patch)I am thinking he is telling you he tested it.

The mbp3 option works for several Macs, this has been confirmed by several people.

If it works, then don't fix it.

---

### Post by puanon on 2008-03-04
> **diddledan said:**
> how can this be tested for an imac when the instructions are clearly for a macbook pro 3? what model should one enter to get things working on an aluminium imac 24inch 2007 machine?

(I'ma stick with nicfagn's patch)

For the new (2007 Aluminium 24'') iMac, i compiled and installed alsa-driver 1.0.16 adding the patch code for the 1.0.15 version.
Internal speakers are working, but not the headphones-line out jack (the signal is very low).
I attach the patch_realtek.c modified file. Rename and replace the existing at /usr/src/modules/alsa-driver/alsa-kernel/pci/hda/ (this is the path in debian, don't know in ubuntu).
Hope this help you.
José A. Pérez

---

### Post by Zarate on 2008-03-04
So, to sum up, sound still does NOT fully work. Not even with ALSA 1.0.16?

I recompiled ALSA 1.0.16, tried make -j3, tried forcing the model to MacBook and everything I've found so far without luck.

My current state is GOOD sound on internal speakers but no sound on headphones at all. Actually, even when headphones are connected internal speakers keep going...

Is this supposed to be fixed in Hardy?

---

### Post by cyberdork33 on 2008-03-04
> **Zarate said:**
> So, to sum up, sound still does NOT fully work. Not even with ALSA 1.0.16?

I recompiled ALSA 1.0.16, tried make -j3, tried forcing the model to MacBook and everything I've found so far without luck.

My current state is GOOD sound on internal speakers but no sound on headphones at all. Actually, even when headphones are connected internal speakers keep going...

Is this supposed to be fixed in Hardy?That is a known bug in the forum, but a patch was needed to fix it... Whether it was reported as a bug against Ubuntu or not I do not know. Things will not get incorporated into new releases unless you file bugs. The devs can't fix it if they don't know it's broken.

Something confuses me though, you say you have no luck, but then you say the sound works... which is it? If it is just the headphone jack that is not working properly then file a bug about it, either directly against ALSA or on launchpad against Ubuntu. If you do file a bug, let everyone else know too so that others experiencing the same issue can add their input.

---

### Post by puanon on 2008-03-04
There are two specific models for iMac 24'' in the path_realtek.c code file i posted.
The older one is named "imac24". It appeared in the imac patch for the 1.0.14 version, and have been included in the official alsa-driver 1.0.16 version.
I found a patch for the 1.0.15 version that added the new iMac 24 model, named "imac-m07" (middle 2007) and i added that code to the 1.0.16 source file.
The result is:
- Internal speakers works fine.
- Headphones sounds at very low level, but internal speakers are muted when attached.

The problem is with alsa-driver, not whit ubuntu or other distro (i have debian and the problem is the same).

Saludos,

José A. Pérez

---

### Post by cyberdork33 on 2008-03-04
> **puanon said:**
> The problem is with alsa-driver, not whit ubuntu or other distro (i have debian and the problem is the same).I am sure that is the case, but you can file a bug in launchpad, and they will make sure the upstream packages are notified.

---

### Post by diddledan on 2008-03-04
well, if it's supposed to be fixed in hardy it isn't. I'm currently running hardy as my main desktop system, for the ati accelerated drivers to work out-of-the-box (after running the restricted drivers installer). However, sound is still a no-go. Once I've read all my backed-up email I'll have a go with nicfagn's patch again to see if I can at least get the internal speakers running.

---

### Post by nicfagn on 2008-03-04
Anyone interested in trying this new patch, just to see if, with this one, the headphones work as expected?

---

### Post by diddledan on 2008-03-04
I've just tried compiling this latest patch, but the compilation fails on hardy. I think this is a hardy/alsa-1.0.15 incompatibility issue, and not a patch issue, as it occurs in ./acore/Makefile:

> make[1]: Entering directory `/usr/src/linux-headers-2.6.24-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/daniel/alsa-driver-1.0.15/acore/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[2]: *** [/home/daniel/alsa-driver-1.0.15/acore] Error 2
make[1]: *** [_module_/home/daniel/alsa-driver-1.0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-11-generic'
make: *** [compile] Error 2

---

### Post by nicfagn on 2008-03-05
> **diddledan said:**
> I've just tried compiling this latest patch, but the compilation fails on hardy. I think this is a hardy/alsa-1.0.15 incompatibility issue, and not a patch issue, as it occurs in ./acore/Makefile:

Yes, I think you are right. Anyway I successfully compiled alsa-1.0.16 in Hardy, so I adjusted the patch for the newer version.
You also have to issue the following command before the 'sudo make install-modules' step: 
```
sudo mv -v /lib/modules/$(uname -r)/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel{,-ubuntu}.ko
```
since in Hardy the ubuntu snd-hda-intel module has a different path.

---

### Post by Kotare on 2008-03-06
nicfagn,
 By following your instructions on page  1 of this post but using your patch alsa-1.0.16.txt and alsa-driver-1-0.16.tar.bz2, I now have sound from the speakers or from the earphone socket on my 24" ali iMac.

Thank you  very much

---

### Post by nicfagn on 2008-03-06
> **Kotare said:**
> 
 By following your instructions on page  1 of this post but using your patch alsa-1.0.16.txt and alsa-driver-1-0.16.tar.bz2, I now have sound from the speakers or from the earphone socket on my 24" ali iMac.
Great news. :)
Unfortunately I can't be sure of what made the headphones work, the port to alsa-1.0.16 or the slight modification I applied to the patch. :-(

---

### Post by diddledan on 2008-03-06
unfortunately, my 24inch aluminium imac remains silent with the latest 1.0.16 patch

---

### Post by diddledan on 2008-03-06
I tried manually forcing the model to both mbp3 (as suggested by an earlier post - didn't think it would work anyway), and imac-m07 in /etc/modprobe.d/alsa-base. neither yielded any sound from either internal or external speakers.

---

### Post by cyberdork33 on 2008-03-06
> **diddledan said:**
> I tried manually forcing the model to both mbp3 (as suggested by an earlier post - didn't think it would work anyway), and imac-m07 in /etc/modprobe.d/alsa-base. neither yielded any sound from either internal or external speakers.

are you sure the channels are unmuted?

---

### Post by e-tip on 2008-03-07
Hi all!
Today i've downloaded alsa-source from hardy (1.0.16) patched it with nicfagn patch and made a deb package. Go [http://www.e-tip.net/blog/2008/02/26/alsa-1016-ubuntu-imac/](http://www.e-tip.net/blog/2008/02/26/alsa-1016-ubuntu-imac/) and in the bottom you'll find the link to download in the bottom of the post

---

### Post by Hataish on 2008-03-07
Hi, This post is very informative, however there are some queries to ask about some specific topic. If someone can help me then please send me a private message. Thanks,

---

### Post by diddledan on 2008-03-07
> **cyberdork33 said:**
> are you sure the channels are unmuted?

this was using nicfagn's patch, btw, and yes the channels were unmuted

---

### Post by cyberdork33 on 2008-03-07
> **e-tip said:**
> Hi all!
Today i've downloaded alsa-source from hardy (1.0.16) patched it with nicfagn patch and made a deb package. Go [http://www.e-tip.net/blog/2008/02/26/alsa-1016-ubuntu-imac/](http://www.e-tip.net/blog/2008/02/26/alsa-1016-ubuntu-imac/) and in the bottom you'll find the link to download in the bottom of the postIt would be best if a bug report could be found / created and the patch posted so that this can get merged into the Ubuntu packages.

Meanwhile, could you request access to the [mactel-support]("https://launchpad.net/%7Emactel-support") commuity in launchpad? We could use an updated package in the ppa repository until it is fixed upstream.

---

### Post by e-tip on 2008-03-07
> **cyberdork33 said:**
> It would be best if a bug report could be found / created and the patch posted so that this can get merged into the Ubuntu packages.

Meanwhile, could you request access to the [mactel-support]("https://launchpad.net/%7Emactel-support") commuity in launchpad? We could use an updated package in the ppa repository until it is fixed upstream.

I can do it, i'm already a member of launchpad, i''ll join mactel-support comunity .
i'll do a bug search in launchpad for see if this bug already exists, thanks for suggestions

---

### Post by cyberdork33 on 2008-03-07
> **e-tip said:**
> I can do it, i'm already a member of launchpad, i''ll join mactel-support comunity .
i'll do a bug search in launchpad for see if this bug already exists, thanks for suggestionsnote there is the mactel-support team (with the ppa) and the mactel-support-community team.

---

### Post by diddledan on 2008-03-08
thankyou e-tip, your .deb package correctly enabled audio on both internal and external speakers.. I now have audio \o/

---

### Post by e-tip on 2008-03-08
> thankyou e-tip, your .deb package correctly enabled audio on both internal and external speakers.. I now have audio \o/

I'm pleased to know that.

---

### Post by diddledan on 2008-03-09
nicfagn, your patch fails to build on xen with the following error:

> make -C /usr/src/linux-headers-2.6.24-12-xen/ SUBDIRS=/home/daniel/alsa-driver-1.0.16  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-xen'
  CC [M]  /home/daniel/alsa-driver-1.0.16/acore/hwdep.o
In file included from /home/daniel/alsa-driver-1.0.16/include/adriver.h:940,
                 from /home/daniel/alsa-driver-1.0.16/acore/hwdep.c:1:
include/linux/pci.h:570: error: expected identifier or ‘(’ before numeric constant
In file included from /home/daniel/alsa-driver-1.0.16/acore/hwdep.c:1:
/home/daniel/alsa-driver-1.0.16/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/daniel/alsa-driver-1.0.16/include/adriver.h:1182: error: too many arguments to function ‘pci_save_state’
/home/daniel/alsa-driver-1.0.16/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/daniel/alsa-driver-1.0.16/include/adriver.h:1186: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/daniel/alsa-driver-1.0.16/acore/hwdep.o] Error 1
make[2]: *** [/home/daniel/alsa-driver-1.0.16/acore] Error 2
make[1]: *** [_module_/home/daniel/alsa-driver-1.0.16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-xen'
make: *** [compile] Error 2

though I would think this either a kernel problem, or an incompatability between alsa and xen generally, rather than due to an issue with the patch, as the errors are reported in the kernel headers, not those of alsa.

looks like I'll have to stick with vmware instead of xen

---

### Post by cyberdork33 on 2008-03-09
> **diddledan said:**
> nicfagn, your patch fails to build on xen with the following error:



though I would think this either a kernel problem, or an incompatability between alsa and xen generally, rather than due to an issue with the patch, as the errors are reported in the kernel headers, not those of alsa.

looks like I'll have to stick with vmware instead of xen
you can easily test your theory by trying to compile alsa without the patch...

---

### Post by nicfagn on 2008-03-10
Sound is broken in linux **2.6.24-12.19**, see [this bug report in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338").
That should be fixed in **2.6.24-12.20** as explained by this changelog:

```
linux (2.6.24-12.20) hardy; urgency=low

  [Ben Collins]

  * Enable CONFIG_SOUND at least, so alsa build in lum works
    - LP: #200338

```

---

### Post by AlexMorin on 2008-03-11
OT : Fedora Core 7 on Alu 24 inch iMac : external speakers work fine with the alsa patch recipe by nicfagn .
My [post]("http://ubuntuforums.org/showpost.php?p=4488075&postcount=114").

Might try a another patch to get the headphone jack volume up.

---

### Post by e-tip on 2008-03-17
Today i've managed to make integrated microphone work (yeah !! )
the only problem is that i have to change input for channel1 to front mic and than put it back to mic to make microphone work

---

### Post by cyberdork33 on 2008-03-22
Please post patches here:
[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/205059](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/205059)

It is best to create patches against latest Ubuntu source packages.

---

### Post by ahappydeath on 2008-04-29
Heres my output from 'make -j3'
any suggestions?

make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/silbermm/Desktop/alsa-driver-1.0.15  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/silbermm/Desktop/alsa-driver-1.0.15/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/home/silbermm/Desktop/alsa-driver-1.0.15/acore] Error 2
make[1]: *** [_module_/home/silbermm/Desktop/alsa-driver-1.0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [compile] Error 2

---

### Post by nicfagn on 2008-04-29
Have a look at [this post]("http://ubuntuforums.org/showpost.php?p=4457201&postcount=37") for the compilation problem.
To make things simple, you can simply use the model=mbp3 option with the snd-hda-intel module shipped with Ubuntu 8.04 as mentioned in [this post]("http://ubuntuforums.org/showpost.php?p=4315166&postcount=26") at point 5.

Bye

Nicola

---

### Post by cyberdork33 on 2008-04-29
> **nicfagn said:**
> Have a look at [this post]("http://ubuntuforums.org/showpost.php?p=4457201&postcount=37") for the compilation problem.
To make things simple, you can simply use the model=mbp3 option with the snd-hda-intel module shipped with Ubuntu 8.04 as mentioned in [this post]("http://ubuntuforums.org/showpost.php?p=4315166&postcount=26") at point 5.
hey, they have combined us with the PPC Macs in a new forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by Cows on 2008-05-17
> **nicfagn said:**
> Yes, I think you are right. Anyway I successfully compiled alsa-1.0.16 in Hardy, so I adjusted the patch for the newer version.
You also have to issue the following command before the 'sudo make install-modules' step: 
```
sudo mv -v /lib/modules/$(uname -r)/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel{,-ubuntu}.ko
```
since in Hardy the ubuntu snd-hda-intel module has a different path.

Thanks this fixed my problem :). I was using 1.0.15 and my computer already had .16.

---

