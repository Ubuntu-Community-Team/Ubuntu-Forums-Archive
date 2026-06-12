---
title: "Installation problems"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Fonikar on 2008-04-21
Hi folks

I'm tearing my hair out trying to get Ubuntu installed!!!

System: ASUS M2NPV-VM MICRO ATX AM2
              ATHLON 64 4000 AM2
              OCZ 1GB (2X512) PC2-5400
              1 x Samsung Spinpoint 160Gb IDE
              2 x Samsung Spinpoint 500Gb SATA300

This system is intended to be used as a MythTV set-up, the mobo has inbuilt graphics and the 500Gb drives are configured in the BIOS as a mirrored RAID. The RAID pair come up as drives 1 and 2  and the IDE as drive 5.

I have tried multiple times to install 8.04 RC but I kept getting GRUB errors (either 21 or 22) having tried all sorts of configurations of partitions etc. I have ended up unplugging the RAID pair, but when I installed it hung after installation and eventually went to BusyBox.

So I gave up on 8.04RC and tried for 7.10. So this time it all installs beautifully, but now I actually boot it up it's incredibly slow and doesn't populate the top bar properly although if I click in the right places it drops down the menus. Opening terminal or any other window results in very slow population of the graphics, if any!

Help would be very much appreciated. I've been at this for 2 days now.

I'm computer savvy but I have no Linux experience, so please assume I know nothing whatsoever.

Thanks in advance.

---

### Post by phidia on 2008-04-21
It could be a video card issue-what is the onboard card? We will need both maker and model.
If you don't know for sure type > lspci -v in the terminal and copy and paste the output. You will also want to know/provide your monitor specs.

---

### Post by Fonikar on 2008-04-21
From this output it looks like the an GeForce 6150.
The monitor I'm currently using to test is an LG 19@ widescreen 1440x900

Here is the output

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fd900000-fd9fffff
        Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
        Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
        Capabilities: <access denied>

00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f7000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f400 [size=16]
        Capabilities: <access denied>

00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at e000 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at cc00 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=128
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f8000000-fbffffff
        Prefetchable memory behind bridge: fdb00000-fdbfffff
        Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81cb
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 816a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c800 [size=8]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at fbfff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fbff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

04:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 9c00 [size=32]
        Capabilities: <access denied>

04:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at 9800 [size=32]
        Capabilities: <access denied>

04:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at fbffe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

04:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Hauppauge computer works Inc. Unknown device 9002
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

04:09.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. Nova-T DVB-T Model 909
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

04:09.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. Nova-T DVB-T Model 909
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

---

### Post by phidia on 2008-04-21
Ok it is an nvidia card be sure you have the correct video driver installed. 
Check or follow [this how to]("http://ubuntuforums.org/showthread.php?t=301499").

---

### Post by Fonikar on 2008-04-21
This is all very well, but I can only actually do anything if I boot up on the live CD as nothing actually works from the install. How would I install the driver to the hard drive if I am running the OS from the CD?

---

### Post by Fonikar on 2008-04-23
Thanks for your help

The problem was the NVidia drivers. both the suggested (by the Ubuntu desktop) one and Envy caused the same failure.

The screen output seems to be ok so far if I just leave things alone.

Thanks again

---

