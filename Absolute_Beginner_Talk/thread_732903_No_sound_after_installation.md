---
title: "No sound after installation"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by thort on 2008-03-23
Hi!

I have just installed Ubuntu 7.10.

I have no sound. Clicking on all test buttons in Sound Preferences gives no sound.

I have a dual boot. In Windows Vista I have sound in my earphones.

What am I to do? Thankful for some assistance!

---

### Post by Sef on 2008-03-23
What are your hardware specs, including sound card?

---

### Post by thort on 2008-03-23
Hi!

I have a **Fujitsu Siemens Scaleo X** desktop computer.

The soundcard is: **Creative Labs SB X-Fi**

I don't know all suitable terminal commands, but here are some I found.


[COLOR="Blue"]thor@thor-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




thor@thor-desktop:~$ lspci -v

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 4f00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at 5000 [size=64]
        I/O ports at 6000 [size=64]
        Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f3fff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f3ffec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        I/O ports at c800 [size=8]
        I/O ports at c480 [size=4]
        I/O ports at c400 [size=8]
        I/O ports at c080 [size=4]
        I/O ports at c000 [size=16]
        Memory at f3ffd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at bc00 [size=8]
        I/O ports at b880 [size=4]
        I/O ports at b800 [size=8]
        I/O ports at b480 [size=4]
        I/O ports at b400 [size=16]
        Memory at f3ffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f8000000-febfffff
        Capabilities: <access denied>

[B]00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at f3ff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

04:08.0 Audio device: Creative Labs SB X-Fi
        Subsystem: Creative Labs Unknown device 6007
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
        Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
        I/O ports at ec00 [size=32]
        Capabilities: <access denied>[/B]

04:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 350d
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
        I/O ports at e880 [size=128]
        Capabilities: <access denied>
[/COLOR]

---

