---
title: "No sound after fresh install"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Tallman on 2007-02-14
Hi all,

I just did a fresh install of Ubuntu 6.10 and there is no sound coming from my speakers.

This problem was there already before the install (I was on Dapper), because I was playing with alsamixer. My sound problems were not the reason for the reinstall, that was because I wanted to install Edgy and change my partitions in the meantime.

But I thought that after a fresh install, my 'wrong' alsamixer settings would have disappeared. Is it normal that these settings survived a re-partitioning, re-formatting and re-install or is this a different problem? If so, any help would be greatly appreciated.

Thanks

---

### Post by cybrkup on 2007-02-14
I've been having sound problems as well since I reinstalled two days ago. If you did a complete reinstall with formating then nothing of the original settings would survive. 

I did find this link that might be helpful: [https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

---

### Post by Tallman on 2007-02-14
Thanks for your reply, cybrkup.

> **cybrkup said:**
> If you did a complete reinstall with formating then nothing of the original settings would survive. 

I thought as much :) 

> **cybrkup said:**
> I did find this link that might be helpful: [https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

Unmuting everything in alsamixer did not help :( 

```
marpau@marpau-desktop:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation Unknown device 01aa (rev b2)
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: 66MHz, fast devsel, IRQ 3
        I/O ports at 24a0 [size=16]
        I/O ports at 24b0 [size=16]
        I/O ports at 2480 [size=32]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3) (prog-if 10 [OHCI])
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at fc800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3) (prog-if 10 [OHCI])
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at fc801000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at fc803000 (32-bit, non-prefetchable) [size=1K]
        I/O ports at 24d0 [size=8]
        Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: fc300000-fc5fffff

00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3) (prog-if 8a [Master SecP PriP])
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 24c0 [size=16]
        Capabilities: <access denied>

00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 66
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=34
        Memory behind bridge: fd000000-fe1fffff
        Prefetchable memory behind bridge: f8000000-fc2fffff

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 8784
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at fc200000 (32-bit, prefetchable) [size=512K]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs Unknown device 806b
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at 1000 [size=32]
        Capabilities: <access denied>

05:06.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at 1020 [size=8]
        Capabilities: <access denied>

05:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
        Subsystem: GVC Corporation Compaq Stinger
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at fc300000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 1028 [size=8]
        Capabilities: <access denied>

05:08.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) (prog-if 10 [OHCI])
        Subsystem: Accton Technology Corporation Unknown device 1394
        Flags: bus master, medium devsel, latency 66, IRQ 185
        Memory at fc314000 (32-bit, non-prefetchable) [size=2K]
        Memory at fc310000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

As you can see, my soundcard is recognized correctly. When I installed Dapper, my sound worked immediately.

Any other ideas?

---

### Post by Tallman on 2007-02-14
Well, I guess we are all entitled to our share of 'blond moments'...

It appeared that the plug was in the wrong connector :redface: :lolflag: 

The good thing is: Ubuntu still rocks!

---

