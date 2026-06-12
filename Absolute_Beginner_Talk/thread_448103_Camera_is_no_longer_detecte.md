---
title: "Camera is no longer detecte"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2007-05-18
It worked fine with Edgy, but not Feisty.

Its a Pnansonic DMC-LZ2.

My USB card reader no longer works.

But my Ipod is still detected.

Any help would be great...

---

### Post by jiminycricket on 2007-05-19
What happens when running in a terminal ```
lspci -v
``` and ```
lsusb
``` with all devices connected?  Do you see any of the hardware that doesn't work listed there?

---

### Post by Icemanyurt on 2007-05-22
Sorry for the delay in response, life kinda went crazy...

Output for lspci -v

> 
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: 66MHz, fast devsel
        I/O ports at 5080 [size=32]
        I/O ports at 5000 [size=64]
        I/O ports at 5040 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ff6fd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at ff6fe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at ff6ffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80a7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ff6fc000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=8]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 812a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at e800 [size=256]
        I/O ports at e400 [size=128]
        Memory at ff6fb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c800 [size=16]
        I/O ports at c400 [size=128]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: ff400000-ff4fffff
        Prefetchable memory behind bridge: ceb00000-eeafffff

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ff500000-ff5fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device c008
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at a800 [size=256]
        Memory at ff4f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ff4c0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device c009
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at ff4e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: ZyXEL Communication Corporation Unknown device 340d
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at b800 [size=256]
        Memory at ff5ffc00 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

02:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 8624
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at ff5df800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>


I am still trying to get the Wifi card and tv turner working,,,but that is another project for another day

Output for lsusb

> 
Bus 003 Device 002: ID 058f:6362 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1310:0001 Roper Class 1 Bluetooth Dongle
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 04da:2372 Panasonic (Matsushita) Lumix DMC-FZ10 Camera
Bus 002 Device 002: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 002 Device 001: ID 0000:0000  


---

