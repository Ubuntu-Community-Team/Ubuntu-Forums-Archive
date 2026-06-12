---
title: "ctrl+alt+F key fails!"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Spectre5 on 2007-04-17
Whenever I press ctrl+alt+F1 (or any F key 1-6) my screen goes all crazy!  I just see green and black boxes all over that move down the screen very quickly.....it doesn't enter the virtual terminal like it should.  If I use F7 it does go back to the desktop like it should.

Any ideas?

---

### Post by AmyRose on 2007-04-17
What video card are you using? And are you on a PC or what?

---

### Post by Spectre5 on 2007-04-17
I am on a PC, an old compaq....

I have an intel integrated graphics card using the i810e driver...with 512 MB of ram (upgarded) and 600 MHz processor speed.

Here is my lspci -v


00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
Subsystem: Compaq Computer Corporation Unknown device b165
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 3
Memory at 44000000 (32-bit, prefetchable) [size=64M]
Memory at 40100000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
I/O behind bridge: 00001000-00001fff
Memory behind bridge: 40000000-400fffff
Prefetchable memory behind bridge: 20000000-200fffff

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
Subsystem: Intel Corporation 82801AA IDE
Flags: bus master, medium devsel, latency 0
I/O ports at 2020 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
Subsystem: Intel Corporation 82801AA USB
Flags: bus master, medium devsel, latency 0, IRQ 11
I/O ports at eec0 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
Subsystem: Intel Corporation 82801AA SMBus
Flags: medium devsel, IRQ 5
I/O ports at eee0 [size=16]

01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
Subsystem: Compaq Computer Corporation Unknown device b19d
Flags: bus master, medium devsel, latency 64, IRQ 5
I/O ports at 1000 [size=256]
Capabilities: <access denied>

01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 3
I/O ports at 1400 [size=256]
Memory at 40000000 (32-bit, non-prefetchable) [size=256]
[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
Capabilities: <access denied>

01:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 01 [Hayes/16450])
Subsystem: PCTel Inc Unknown device 0001
Flags: medium devsel, IRQ 11
I/O ports at 1800 [size=64]
Capabilities: <access denied>




Any other information that might help?

---

### Post by Spectre5 on 2007-04-19
Anyone have any idea of why this would happen (or experienced it before themselves...so I know I'm not alone :) )

---

### Post by bertilow on 2007-04-19
I see things like that sometimes when I shut down the computer. Looks really strange (psychedelic) sometimes. But it's no real problem.

---

### Post by Spectre5 on 2007-04-19
That is exactly what I get when I start or shut down my computer....but I also get it when going into a virtual terminal...

---

### Post by Spectre5 on 2007-04-22
Upgrade to feisty fixed this issue for me!

-Scott

---

