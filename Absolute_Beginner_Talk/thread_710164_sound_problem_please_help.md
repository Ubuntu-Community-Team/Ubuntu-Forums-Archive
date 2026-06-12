---
title: "sound problem please help"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-02-28
I persuaded my brother to let me install ubuntu on his laptop. I thought I`d checked everything on the live cd so I nuked windows completely. I forgot to check sound.
 It`s a Toshiba Equium A210-17I.
 I`ve been through tutorials and how tos but I can`t get it working.
This is the output of  aplay -l

aplay: device_list:204: no soundcards found...


This is the output of lspci -v

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f8000000-f81fffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f8200000-f82fffff
        Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0e, subordinate=13, sec-latency=0
        Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
        I/O ports at 8440 [size=8]
        I/O ports at 8434 [size=4]
        I/O ports at 8438 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8400 [size=16]
        Memory at f8609000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at f8604000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f8605000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at f8606000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f8607000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at f8608000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at f8609400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8420 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Toshiba America Info Systems Unknown device ff0a
        Flags: bus master, slow devsel, latency 64, IRQ 10
        Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=14, subordinate=19, sec-latency=64
        Memory behind bridge: f8300000-f83fffff

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

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff1a
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at f0000000 (64-bit, prefetchable) [size=128M]
        Memory at f8100000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 9000 [size=256]
        Memory at f8000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at a000 [size=256]
        Memory at f8200000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at f8300000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8300800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8300c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8301000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8301400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>


Any help would be greatly appreciated.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

Built in wireless doen`t work by the way but we`ve got a usb thingy that does so that`s not a major problem.
:)

---

### Post by nothingspecial on 2008-02-28
I`ve also managed to remove alsamixer somehow. Can anyone help?:)

---

### Post by spamzilla on 2008-02-28
Open up synaptics and search for 'alsa' or 'alsa-mixer' or maybe even 'alsa-base' - sorry I cannot remember the package name, but it should be pretty obvious when you see it. When you find it, click install and then apply - good luck :)

---

### Post by smurphy_it on 2008-02-28
Well according to your post your audio controller is:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia

Another useful link which might help in getting your HD audio controller working is the following linke.

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

