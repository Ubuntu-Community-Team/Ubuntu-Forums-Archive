---
title: "Everything working but sound....."
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by paul6888 on 2008-01-15
I finally got everything working on this dang laptop except the sound, which Windows just referred to as Realtek AC97 CODEC. I no longer use WinDOS (not even as dual-boot) in favor of Ubuntu 7.04, so no sound at all. Not even the motherboard makes a peep. Can someone help me? I can't even watch the 2008 Macworld keynote on this thing.

---

### Post by paul6888 on 2008-01-15
Followed some instructions, should be restarting soon.......

---

### Post by paul6888 on 2008-01-15
No use, still no sound.

---

### Post by wjp.reg on 2008-01-15
what's your output for

```
lspci -v
```?

---

### Post by paul6888 on 2008-01-15
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fa100000-fa8fffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000bfefffff
        Capabilities: <access denied>

00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2) (prog-if 00 [VGA])
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Rioworks Unknown device 205e
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at b0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 3080 [size=16]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=64
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: b3400000-b34fffff
        Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Rioworks Unknown device 205e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3090 [size=8]
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

06:09.0 Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC
        Subsystem: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 6000 [size=256]
        I/O ports at 6400 [size=128]
        Memory at b3400000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

Pretty freakin' long, eh? Also it's pretty easy to tell I have an nForce motherboard.

---

### Post by paul6888 on 2008-01-15
Uh....... hello????? God, what I would give for a MacBook Air and a Time Capsule right now.

.......Speaking of which, I'm trying to make this thing look like Vista. Anyone have an alternative to Segoe UI (and how do you install fonts anyway)?

---

### Post by wjp.reg on 2008-01-16
> 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
Subsystem: Rioworks Unknown device 205e
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

If you do a google search on ```
ubuntu and nVidia Corporation MCP51 High Definition Audio
``` you'll find that there are lots of people that can't get this card running in ubuntu; calling it a "bug", as it used to run under feisty.

One suggestion, if it's a desktop, is to swap in SoundBlaster card; that's what I had to do.  Otherwise, keep searching and praying ;-)

good luck

---

### Post by paul6888 on 2008-01-16
I use a laptop with Feisty, but I can put an ExpressCard/54 SoundBlaster in it. But can you show me how to get the onboard sound working? (Yay, I just got an iPod Touch!)

---

### Post by paul6888 on 2008-01-18
Why the #3!! isn't anyone answering me?!?!!?!?

---

