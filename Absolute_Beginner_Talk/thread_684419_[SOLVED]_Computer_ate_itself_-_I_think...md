---
title: "[SOLVED] Computer ate itself - I think.."
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-01
So I was using my computer - and I went to minimize, and firefox jammed and I lost GUI display and it went into the shell then came back with an "X" about 10 seconds later with an error msg saying that my vid card cannot be detected and until it is I can't use higher screen res, etc.

I restarted, same error msg.  It sounds like my (new) video card crapped out - but when I view a movie or something full screen it runs fine...glxgears doesn't work - I tried reinstalling nvidia drivers with Envy but that didn't go anywhere.  Though everything appears to be fine - usually when something's up with your vid card if you shake a window too fast it lags, or sometimes the mouse jumps, but none of that - it's running fine - but maxing at 800x600 res?

I don't have a screwdriver here but I'm going to re-seat the video card tomorrow - does this sound like a video card problem or does it sound like something happened?  'Cause usually if you lose contact with the vid card like that the "desktop interface" isn't "smooth" if ya get what I mean.

TIA

EDIT:
I explained it really poorly - but you shouldn't be able to view a movie full screen with no vid problems in the least if it's not recognizes your vid card even enough to implement the drivers - which is why this problem seems confusing to me.

---

### Post by The Tronyx on 2008-02-01
Hungry computers happen man!  Nothing you can do about it unfortunately =/





Just kidding.  Did you try reconfiguring X?
> 
sudo dpkg-reconfigure -phigh xserver-xorg


---

### Post by indytim on 2008-02-01
If you have a "flavor" of Windows still installed, try booting to it and see if it exhibits video problems.  If so, you've just isolated it to a hardware problem and not linked to you ops.  Best to resolve the hardware before you "dink" around with the ops.

IndyTim

---

### Post by polmir on 2008-02-01
type in terminal
```
lspci -vv
```
and post out of it

---

### Post by Syndacate on 2008-02-01
> **polmir said:**
> type in terminal
```
lspci -vv
```
and post out of it

I don't think that'll do much - it's an AGP card (yeah, my computer is archaic, but the vid card is only 4 weeks old...I bought it at the end of week 3 of school and now it's end of week 7 - and the temps are fine - :(.

Somebody mentioned windows - I forgot I had windows on there - I'll boot into windows and see if the problem persists.

---

### Post by Syndacate on 2008-02-01
Alright, so I booted windows and the video worked 100%.

It was set to my regular setting of 1920x1200 resolution - no skipping, video displayed 100% on movies, and it was recognized in the device manager w/o any errors.

So I guess it's an ubuntu only problem - it still boots into "low graphics mode" - and I did install the nvidia driver with Envy to no avail.

Gah, this sucks, this is my first major linux breakdown and I have no idea what to do :(

---

### Post by dannyboy79 on 2008-02-01
what nvidia module are you using

dmesg | grep NV

then also, what does this return when you enter it in the terminal?

cat /etc/X11/xorg.conf | grep Driver

also, just because your card is AGP doesn't mean that lspci won't show us the card type. everything is pretty much connected to the PCI bus.

---

### Post by Syndacate on 2008-02-01
> **dannyboy79 said:**
> what nvidia module are you using

dmesg | grep NV

then also, what does this return when you enter it in the terminal?

cat /etc/X11/xorg.conf | grep Driver

also, just because your card is AGP doesn't mean that lspci won't show us the card type. everything is pretty much connected to the PCI bus.

**dmesg | grep NV** displayed this:
```

$ dmesg | grep NV
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[   48.086359] nvidia: module license 'NVIDIA' taints kernel.
[   48.338637] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.07  Thu Dec 13 18:42:56 PST 2007
[   63.058402] NVRM: API mismatch: the client has the version 169.09, but
[   63.058404] NVRM: this kernel module has the version 169.07.  Please
[   63.058406] NVRM: make sure that this kernel module and all NVIDIA driver
[   63.058407] NVRM: components have the same version.
[   67.141605] NVRM: API mismatch: the client has the version 169.09, but
[   67.141608] NVRM: this kernel module has the version 169.07.  Please
[   67.141609] NVRM: make sure that this kernel module and all NVIDIA driver
[   67.141610] NVRM: components have the same version.
[   71.195477] NVRM: API mismatch: the client has the version 169.09, but
[   71.195479] NVRM: this kernel module has the version 169.07.  Please
[   71.195481] NVRM: make sure that this kernel module and all NVIDIA driver
[   71.195482] NVRM: components have the same version.
[  104.055476] NVRM: API mismatch: the client has the version 169.09, but
[  104.055478] NVRM: this kernel module has the version 169.07.  Please
[  104.055479] NVRM: make sure that this kernel module and all NVIDIA driver
[  104.055481] NVRM: components have the same version.

```

**cat /etc/X11/xorg.conf | grep Driver** Displayed this:
```

$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "nvidia"

```

**lspci -vv** displayed this:
```

00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: e0000000-efffffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fd000000-fd0fffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: Memory at fd101000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 4: I/O ports at bc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 18
        Region 4: I/O ports at b000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 16
        Region 4: I/O ports at b400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 4: I/O ports at b800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 19
        Region 0: Memory at fd100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: 50000000-500fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at f000 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 11
        Region 4: I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2) (prog-if 00 [VGA])
        Subsystem: Unknown device 196e:0380
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Region 2: Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (63750ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=128K]
        Region 2: I/O ports at a000 [size=32]
        Capabilities: <access denied>

03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fc005000 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at fc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

03:03.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
        Subsystem: Silicon Image, Inc. SiI 3112 SATARaid Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at 8000 [size=8]
        Region 1: I/O ports at 8400 [size=4]
        Region 2: I/O ports at 8800 [size=8]
        Region 3: I/O ports at 8c00 [size=4]
        Region 4: I/O ports at 9000 [size=16]
        Region 5: Memory at fc004000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 50000000 [disabled] [size=512K]
        Capabilities: <access denied>

03:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: ADMtek Unknown device 0574
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (16000ns min, 32000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at 9400 [size=256]
        Region 1: Memory at fc006000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 50080000 [disabled] [size=128K]
        Capabilities: <access denied>

03:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
        Subsystem: Creative Labs CT4850 SBLive! Value
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at 9800 [size=32]
        Capabilities: <access denied>

03:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 01)
        Subsystem: Creative Labs Gameport Joystick
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Region 0: I/O ports at 9c00 [size=8]
        Capabilities: <access denied>

```

It displayed a ******** of stuff...

I don't know what half of it means, but it seems as though it doesn't know what the hell my vid card is :-\

---

### Post by cubeist on 2008-02-01
Your use of envy on top of existing nvidia kernel modules is causing confusion...  If I remember correctly, there is a hidden file that you may need to temporarily move... I'll go look

Ok... at /lib/linux-restricted-modules there is a hidden file called .nvidia_new_installed, or something like that.

DO Not delete this file, instead, just rename it something different so the computer can't see it when you reboot.  If you reboot ok then leave things alone, if you have more problems booting, go back and rename the file to the original name so the computer can see it... 

I hope this helps... there is a tutorial floating around somewhere with better instructions than I just posted but I can't find it...

---

### Post by polmir on 2008-02-01
> **lspci**  is a utility for displaying information about all PCI buses in the system and all devices connected to them.
type in terminal
```

man lspci
man xorg.conf
man grep
man cat

```
this is info about your  video card
> ```
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2) (prog-if 00 [VGA])
        Subsystem: Unknown device 196e:0380
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Region 2: Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <access denied>
```


==========================
>>My Linux is better for my English<<

---

### Post by dannyboy79 on 2008-02-01
> **Syndacate said:**
> **dmesg | grep NV** displayed this:
```

$ dmesg | grep NV
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[   48.086359] nvidia: module license 'NVIDIA' taints kernel.
[   48.338637] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.07  Thu Dec 13 18:42:56 PST 2007
[   63.058402] NVRM: API mismatch: the client has the version 169.09, but
[   63.058404] NVRM: this kernel module has the version 169.07.  Please
[   63.058406] NVRM: make sure that this kernel module and all NVIDIA driver
[   63.058407] NVRM: components have the same version.
[   67.141605] NVRM: API mismatch: the client has the version 169.09, but
[   67.141608] NVRM: this kernel module has the version 169.07.  Please
[   67.141609] NVRM: make sure that this kernel module and all NVIDIA driver
[   67.141610] NVRM: components have the same version.
[   71.195477] NVRM: API mismatch: the client has the version 169.09, but
[   71.195479] NVRM: this kernel module has the version 169.07.  Please
[   71.195481] NVRM: make sure that this kernel module and all NVIDIA driver
[   71.195482] NVRM: components have the same version.
[  104.055476] NVRM: API mismatch: the client has the version 169.09, but
[  104.055478] NVRM: this kernel module has the version 169.07.  Please
[  104.055479] NVRM: make sure that this kernel module and all NVIDIA driver
[  104.055481] NVRM: components have the same version.

```

**cat /etc/X11/xorg.conf | grep Driver** Displayed this:
```

$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "nvidia"

```

**lspci -vv** displayed this:
```

00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: e0000000-efffffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fd000000-fd0fffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: Memory at fd101000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 4: I/O ports at bc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 18
        Region 4: I/O ports at b000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 16
        Region 4: I/O ports at b400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 4: I/O ports at b800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 19
        Region 0: Memory at fd100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: 50000000-500fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at f000 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 11
        Region 4: I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2) (prog-if 00 [VGA])
        Subsystem: Unknown device 196e:0380
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Region 2: Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (63750ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=128K]
        Region 2: I/O ports at a000 [size=32]
        Capabilities: <access denied>

03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1014
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fc005000 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at fc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

03:03.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
        Subsystem: Silicon Image, Inc. SiI 3112 SATARaid Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at 8000 [size=8]
        Region 1: I/O ports at 8400 [size=4]
        Region 2: I/O ports at 8800 [size=8]
        Region 3: I/O ports at 8c00 [size=4]
        Region 4: I/O ports at 9000 [size=16]
        Region 5: Memory at fc004000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 50000000 [disabled] [size=512K]
        Capabilities: <access denied>

03:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: ADMtek Unknown device 0574
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (16000ns min, 32000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at 9400 [size=256]
        Region 1: Memory at fc006000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 50080000 [disabled] [size=128K]
        Capabilities: <access denied>

03:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
        Subsystem: Creative Labs CT4850 SBLive! Value
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at 9800 [size=32]
        Capabilities: <access denied>

03:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 01)
        Subsystem: Creative Labs Gameport Joystick
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Region 0: I/O ports at 9c00 [size=8]
        Capabilities: <access denied>

```

It displayed a ******** of stuff...

I don't know what half of it means, but it seems as though it doesn't know what the hell my vid card is :-\
temporarily use vesa in your xorg.conf. do a ctrl-alt-backspace to restart x. you should be able to use Envy and remove all nvidia drivers. then use synaptic and remove all nvida stuff.  then use Envy again to install and you should be fine. also, I am pretty sure the author of Envy has a troubleshooting page on his website which may have the answer regarding API mismatch error. I dealt with awhile ago when mixing the restricted module manager and envy.

---

### Post by ~LoKe on 2008-02-01
Looks like you tried installing the restricted drivers two different ways (probably with nvidia-glx-new and envy, or perhaps the binary installer).
```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```
Then re-install the drivers.

---

### Post by Syndacate on 2008-02-01
I tried uninstalling with Envy then removing the .nvidia_new_installed - then reinstlaled with Envy - no go.

I tried temporarily renaming it and restarted it, no-go.

In synaptic there's a bunch of stuff checked off under a search for "nvidia" - I'm not sure which stuff to remove and which not to, I got:

- linux-restricted-modules-2.6.22-14-generic
- envy
- nvidia-glx-new
- nvidia-glx-new-dev
- nvidia-kernel-2.6.22-14-generic
- nvidia-kernel-common
- nvidia-new-kernel-source
- restricted-manager
- restricted-manager-core
- restricted-manager-kde
- smartdimmer
- trigger
- trigger-data
- xserver-xorg-video-nv

I'm not sure which ones to remove - obviously I'm a little hesitant about removing stuff with the word "kernel" in it.

It seems that there's a driver confusion - which is great.

Though I feel some of you have gotten the impression that I was messing around with the drivers and it went downhill from there - which simply ISN'T the case.

I had a bit of trouble finding the drivers for it - I tried Envy but to no avail, I uninstalled the ones from Envy and ended up using some restricted module crap which had "insert itself into the kernel" or some ******** like that.  In any event - that was a month or so ago.

This **** all just happened last night - as I was closing firefox - it's not like I was messing with the drivers or anything - it was all working fine..

---

### Post by Syndacate on 2008-02-02
Finally got it fixed.

After all the ********, after messing around, I narrowed down that it only happened when I had a driver installed - when Envy and restricted were both disabled - it booted the OEM nv driver and ran fine - but of course the rendering sucked.

My friend and I were troubleshooting for a bit and he figured out that a module was corrupt.

So I asked him the commands to just take all the nvidia crap off and put it back on.

He replied with:

```

sudo apt-get remove nvidia*

```

```

sudo apt-get install nvidia-glx-new

```

Restarted, works 100%.

Thanks guys.  Sometimes the fixes are amazingly simple.

---

### Post by dannyboy79 on 2008-02-04
> **Syndacate said:**
> Finally got it fixed.

After all the ********, after messing around, I narrowed down that it only happened when I had a driver installed - when Envy and restricted were both disabled - it booted the OEM nv driver and ran fine - but of course the rendering sucked.

My friend and I were troubleshooting for a bit and he figured out that a module was corrupt.

So I asked him the commands to just take all the nvidia crap off and put it back on.

He replied with:

```

sudo apt-get remove nvidia*

```

```

sudo apt-get install nvidia-glx-new

```

Restarted, works 100%.

Thanks guys.  Sometimes the fixes are amazingly simple.

glad you did what I suggested...........

my statement "then use synaptic and remove all nvida stuff"

---

