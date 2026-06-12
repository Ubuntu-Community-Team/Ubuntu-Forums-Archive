---
title: "Buffalo Wireless Problem"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by VTStevenVT on 2006-07-03
Alright i'm not a complete linux noob, but still in my first month with ubuntu, used fedora for about month some time ago.

I followed ndiswrapper stuff because my wireless care was not recognized by ubuntu.

Couldn't even get ndiswrapper to work. Did some digging around and found the command I was looking for: lspci -v
I found something kinda strange. my wireless card isn't seen AT all. I'm dual booting ubuntu and windows xp and i have my card configured and working under windows, so I know the wireless card/Pci slot is functional.

My wireless card: 
Buffalo Turbo G Wireless Desktop PCI Adapter (WLI2-PCI-G54S )

Any Ideas??

Here is the output of my lspci -v: 

[I][I]
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81d2
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81d2
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81d2
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81d2
        Flags: 66MHz, fast devsel

0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81d2
        Flags: 66MHz, fast devsel

0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fa600000-fa7fffff
        Capabilities: <available only to root>

0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fa800000-fa8fffff
        Capabilities: <available only to root>

0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <available only to root>

0000:00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at ec00 [size=32]
        I/O ports at 0600 [size=64]
        I/O ports at 0700 [size=64]
        Capabilities: <available only to root>

0000:00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 58
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        I/O ports at e400 [size=256]
        I/O ports at e000 [size=256]
        Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at ffa0 [size=16]
        Capabilities: <available only to root>

0000:00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at dc00 [size=8]
        I/O ports at d880 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=16]
        Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        I/O ports at d080 [size=8]
        I/O ports at d000 [size=4]
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=16]
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fa900000-fa9fffff
        Prefetchable memory behind bridge: bfe00000-bfefffff

0000:00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c480 [size=8]
        Capabilities: <available only to root>

0000:00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <available only to root>

0000:00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: faa00000-feafffff
        Prefetchable memory behind bridge: 00000000bff00000-00000000dfe00000
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

0000:01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8177
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at fa7ffc00 (64-bit, non-prefetchable) [size=128]
        Memory at fa7f8000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 8c00 [size=128]
        Expansion ROM at fa700000 [disabled] [size=512K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 15)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet Controller (Asus)
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at fa8fc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 9800 [size=256]
        Expansion ROM at fa8c0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:04:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 64, IRQ 74
        I/O ports at a880 [size=64]
        Capabilities: <available only to root>

0000:04:06.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 64
        I/O ports at ac00 [size=8]
        Capabilities: <available only to root>

0000:04:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 64, IRQ 66
        Memory at fa9ff800 (32-bit, non-prefetchable) [size=2K]
        Memory at fa9f8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:04:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: LeadTek Research Inc.: Unknown device 6609
        Flags: bus master, medium devsel, latency 64, IRQ 90
        Memory at bfefe000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:04:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: LeadTek Research Inc.: Unknown device 6609
        Flags: bus master, medium devsel, latency 64, IRQ 90
        Memory at bfeff000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, medium devsel, latency 64, IRQ 74
        Memory at fa9ff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fa9f4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:06:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0291 (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc.: Unknown device 2213
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at bc00 [size=128]
        Expansion ROM at feae0000 [disabled] [size=128K]
        Capabilities: <available only to root>[/I][/I]

---

### Post by Apple 101 on 2006-07-04
Do you see anything about your wireless card when using the *dmesg* command?  For ndiswrapper to work correctly, you will need the Windows .inf and .sys files for your card.

---

### Post by cmichaelboyd on 2006-09-14
run it as root:

su lspci -v


and print the output here


-Christopher

---

