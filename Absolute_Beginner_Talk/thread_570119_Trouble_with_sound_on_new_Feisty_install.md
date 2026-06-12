---
title: "Trouble with sound on new Feisty install"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Mileeta on 2007-10-07
I just put a new install of Ubuntu 7.04 on my computer.  I have tried following the steps given in the sound troubleshooting guide, but I'm doing something wrong, because it isn't working.  I'm not sure which terminal texts I should include, so here's a couple to start.

```

chris@chris-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SBLive! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Platinum [CT4760P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@chris-desktop:~$ 

chris@chris-desktop:~$ lspci -v
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: ALi Corporation AGP8X Controller (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: a8000000-a80fffff

00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, medium devsel, latency 32

00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Giga-byte Technology Unknown device 5003
        Flags: medium devsel

00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
        Subsystem: Giga-byte Technology Unknown device ae01
        Flags: bus master, medium devsel, latency 32, IRQ 12
        I/O ports at d000 [size=256]
        Memory at fc000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7) (prog-if fa)
        Subsystem: Giga-byte Technology Unknown device 5002
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]

00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10) (prog-if 8f)
        Subsystem: Giga-byte Technology Unknown device b003
        Flags: bus master, 66MHz, medium devsel, latency 128, IRQ 16
        I/O ports at d400 [size=8]
        I/O ports at d800 [size=4]
        I/O ports at dc00 [size=8]
        I/O ports at e000 [size=4]
        I/O ports at e400 [size=16]

00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        Memory at fc001000 (32-bit, non-prefetchable) [size=4K]

00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        Memory at fc002000 (32-bit, non-prefetchable) [size=4K]

00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at fc003000 (32-bit, non-prefetchable) [size=4K]

00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 48, IRQ 21
        Memory at fc004000 (32-bit, non-prefetchable) [size=256]
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

01:00.0 VGA compatible controller: nVidia Corporation NV38 [GeForce FX 5950 Ultra] (rev a1) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 01c6
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 22
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at f9000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
        Subsystem: Creative Labs CT4760 SBLive!
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

02:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at c400 [size=8]
        Capabilities: <access denied>

02:07.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10 [OHCI])
        Subsystem: Agere Systems FW323
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at fb001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: ADMtek Unknown device 0574
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at c800 [size=256]
        Memory at fb000000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at a8000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at cc00 [size=256]
        Memory at fb002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

chris@chris-desktop:~$ 

chris@chris-desktop:~$ sudo modprobe snd-emu10k1
Password:
chris@chris-desktop:~$ 


```

I do all of that, there is still no sound.  I check that I am not muted in alsamixer, there is still no sound.  There was sound in Windows, but I can't do anything about that now because I went all in and just wiped it out.

If anyone can help, that'd be great.

---

### Post by linuxwizard on 2007-10-07
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF. 

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab

---

### Post by Mileeta on 2007-10-08
Well, I didn't know that was there!  It worked, thank you so much!

---

### Post by linuxwizard on 2007-10-08
That's great it worked and fixed your issue. I have a Creative sound card also every install i do I have to go and change the switches no sound till I do. 

Please mark thread solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

