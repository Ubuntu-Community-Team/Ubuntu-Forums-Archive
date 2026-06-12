---
title: "No Audio can anyone help me out?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by gingerj on 2007-02-10
Hi all, up until now if I wanted to listen to an MP3 I'd have to boot into my XP partition. So I thought this morning I'll finally sort out MP3 support as all my podcast's and albums are all on mp3 format. I've been restricted so far to listen to anything via Ubuntu.

So I read the RestrictedFormats wiki, opened up Synaptic and downloaded the suggested package gstreamer0.10-fluendo-mp3.

I then opened up Rhythmbox and opened up an MP3 I just downloaded as a test. It says that the mp3 is playing but I head no sound from my laptop.

I checked to see if the volume was up in Ubuntu and that's fine, so I'm not sure how to fix this issue. Can anybody help?

---

### Post by mspendlo on 2007-02-10
You can run and hear the test sounds in system->preferences->sound and have the audio device configured for music playback ?

---

### Post by xpod on 2007-02-10
applications>accesories>terminal and type in "alsamixer"

Check nothing you need is tuned down or muted.
"m" key to unmute btw:)

---

### Post by gingerj on 2007-02-10
> **mspendlo said:**
> You can run and hear the test sounds in system->preferences->sound and have the audio device configured for music playback ?

I turned everything up and nothing go played.

> **mspendlo said:**
> You can run and hear the test sounds in system->preferences->sound and have the audio device configured for music playback ?

I tested a sound sample and nothing came out.

Well confused?

---

### Post by gingerj on 2007-02-10
Reading some peoples help threads some people have used the aplay -l command:

Does anyone notice anything shocking here?

> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by gingerj on 2007-02-10
Also this command but it throws a HUGE page of details which I'm baffled by:

> 
lspci -v
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03 )
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev  03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c8100000-c81fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d7f00000
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 52000000-520fffff
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <available only to root>

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 66
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1840 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co ntroller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 66
        Memory at c8004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (pro g-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=56
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c8300000-c83fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000051f00000
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg e (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controlle r (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1880 [size=16]

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev  02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 714 9 (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at c8120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
        Subsystem: Intel Corporation: Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at 52000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at 3000 [size=256]
        Memory at c8300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 168, IRQ 201
        Memory at c8301000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 54000000-55fff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 57, IRQ 10
        Memory at c8302000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:0a:09.3 0805: Texas Instruments: Unknown device 803c (prog-if 01)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0094
        Flags: bus master, medium devsel, latency 57, IRQ 201
        Memory at c8300400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>


Do people actually understand all this stuff that gets thrown out when you type a command via the terminal. It confuses me so so much.

---

### Post by gingerj on 2007-02-11
Hi all, sorry to bump this thread but could anyone shed some light on this problem please?

---

### Post by gingerj on 2007-02-12
Hi all sorry to pester, but could anyone help me out on this problem. I'm not totally sure what the output I've been given helps or if I need to install drivers manually and if so how/where.

Err I'm confused :confused: :confused: :confused:

---

