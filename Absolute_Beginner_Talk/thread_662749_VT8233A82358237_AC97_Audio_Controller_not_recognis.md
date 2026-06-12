---
title: "VT8233/A/8235/8237 AC97 Audio Controller not recognised"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Frogster on 2008-01-09
I am hoping that someone can help me with this problem. I have installed Ubuntu and have succeeded in setting up networking and printing but sound has beaten me.

The problem probably has a very quick work around but I cant see it and reading through the documentation has left me unable to see the wood for the trees!

I have listed the PCI's used. However, if any other information is required please ask as I really need sound to work prior to rolling Ubuntu out across the network!

Thank you for any help in advance

keith@keith-Ubuntu:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: e0000000-e7ffffff
        Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
        Subsystem: ABIT Computer Corp. KV7
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at b000 [size=8]
        I/O ports at b400 [size=4]
        I/O ports at b800 [size=8]
        I/O ports at bc00 [size=4]
        I/O ports at c000 [size=16]
        I/O ports at c400 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 16
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at c800 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at ea000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: medium devsel, IRQ 20
        I/O ports at dc00 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at e000 [size=256]
        Memory at ea001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at e9000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

