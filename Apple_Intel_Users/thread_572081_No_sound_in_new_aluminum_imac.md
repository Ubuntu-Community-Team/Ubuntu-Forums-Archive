---
title: "No sound in new aluminum imac"
date: 2007-10-10
forum: Apple Intel Users
---

### Post by Askrates on 2007-10-10
Hi all,

I have just installed the latest build of Gutsy (9th october), and everything except sound works. This seems to be reported by a number of people, but with no solution that works.

The problem is that sound is no more than a very, very faint whisper. I have tried setting everything to max in alsamixer, tried testing with headphones, tried compiling the newest alsa-driver-1.0.15 release candidate 3, and tried asking on the forums.

If anyone can post some instructions that work, I will give them my daughters hand and half my kingdom :)  

The hardware in the new imac is
- REALTEK ALC885
- HDA Intel

Cheers!

---

### Post by nicfagn on 2007-10-10
You can try to follow these [instructions]("http://ubuntuforums.org/showpost.php?p=2978364&postcount=41") posted in this [thread]("http://ubuntuforums.org/showthread.php?t=418681"), applying this [patch]("http://ubuntuforums.org/showpost.php?p=3461493&postcount=82") instead.
Can you report back exactly what works for you? Thanks.

Ciao

Nicola

---

### Post by Askrates on 2007-10-10
Thanks for the Nicola,

I followed the instructions, but it didn't help. I still have very weak sound in the headphones and no sound in the built in speakers.

Any ideas?

---

### Post by nicfagn on 2007-10-11
Can you post the output of the following commands?

- sudo lspci -nv
- cat /proc/asound/version
- cat /proc/asound/card0/codec#0
- amixer

Thanks

Nicola

---

### Post by Askrates on 2007-10-11
Sure, here you go:
[B]
sudo lspci -nv[/B]

00:00.0 0600: 8086:2a00 (rev 03)
        Subsystem: 106b:00a0
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 0604: 8086:2a01 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 90600000-906fffff
        Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
        Capabilities: [88] Subsystem: 8086:0000
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 0c03: 8086:2834 (rev 03) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 40c0 [size=32]

00:1a.1 0c03: 8086:2835 (rev 03) (prog-if 00 [UHCI])
        Subsystem: 106b:00a0
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 40a0 [size=32]

00:1a.7 0c03: 8086:283a (rev 03) (prog-if 20 [EHCI])
        Subsystem: 106b:00a0
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at 90704c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 0403: 8086:284b (rev 03)
        Subsystem: 106b:00a0
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at 90700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 0604: 8086:283f (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 90500000-905fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: 0000:0000
        Capabilities: [a0] Power Management version 2

00:1c.3 0604: 8086:2845 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 90400000-904fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: 0000:0000
        Capabilities: [a0] Power Management version 2

00:1c.4 0604: 8086:2847 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: 90300000-903fffff
        Prefetchable memory behind bridge: 0000000090000000-00000000900fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: 0000:0000
        Capabilities: [a0] Power Management version 2

00:1c.5 0604: 8086:2849 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 90200000-902fffff
        Prefetchable memory behind bridge: 0000000090800000-00000000908fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: 0000:0000
        Capabilities: [a0] Power Management version 2

00:1d.0 0c03: 8086:2830 (rev 03) (prog-if 00 [UHCI])
        Subsystem: 106b:00a0
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 4080 [size=32]

00:1d.1 0c03: 8086:2831 (rev 03) (prog-if 00 [UHCI])
        Subsystem: 106b:00a0
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 4060 [size=32]

00:1d.2 0c03: 8086:2832 (rev 03) (prog-if 00 [UHCI])
        Subsystem: 106b:00a0
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 4040 [size=32]

00:1d.7 0c03: 8086:2836 (rev 03) (prog-if 20 [EHCI])
        Subsystem: 106b:00a0
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at 90704800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 0604: 8086:2448 (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        Memory behind bridge: 90100000-901fffff
        Capabilities: [50] Subsystem: 0000:0000

00:1f.0 0601: 8086:2815 (rev 03)
        Subsystem: 106b:00a0
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 0101: 8086:2850 (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: 106b:00a0
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 40e0 [size=16]

00:1f.2 0101: 8086:2828 (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: 106b:00a0
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at 40f8 [size=8]
        I/O ports at 4114 [size=4]
        I/O ports at 40f0 [size=8]
        I/O ports at 4110 [size=4]
        I/O ports at 4020 [size=16]
        I/O ports at 4000 [size=16]
        Capabilities: [70] Power Management version 3

00:1f.3 0c05: 8086:283e (rev 03)
        Subsystem: 106b:00a0
        Flags: medium devsel, IRQ 10
        Memory at 90705000 (32-bit, non-prefetchable) [size=256]
        I/O ports at efa0 [size=32]

01:00.0 0300: 1002:94c8 (prog-if 00 [VGA])
        Subsystem: 106b:0084
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        Memory at 90620000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 3000 [size=256]
        Expansion ROM at 90600000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint IRQ 0
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

03:00.0 0c00: 11c1:5901 (rev 05) (prog-if 10 [OHCI])
        Subsystem: 11c1:5900
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 90400000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 3
        Capabilities: [4c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [60] Express Endpoint IRQ 0

04:00.0 0280: 14e4:4328 (rev 03)
        Subsystem: 106b:0088
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at 90300000 (64-bit, non-prefetchable) [size=16K]
        Memory at 90000000 (64-bit, prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

05:00.0 0200: 11ab:436a (rev 13)
        Subsystem: 11ab:00ba
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 90200000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        Expansion ROM at 90800000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

**cat /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Oct 12 2007 for kernel 2.6.22-14-generic (SMP).

**cat /proc/asound/card0/codec#0**
Codec: Realtek ALC885
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3000
Revision Id: 0x100103
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x93 0x93] [0x00 0x00] [0x1b 0x1b] [0x00 0x00] [0x00 0x00] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x90100140: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x012b4050: [Jack] HP Out at Ext Rear
    Conn = Comb, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x083c: IN OUT HP Detect
  Pin Default 0x90100141: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x90a00110: [Fixed] Mic at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x24: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x018b3020: [Jack] Line In at Ext Rear
    Conn = Comb, Color = Blue
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x014be060: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = White
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x0820: IN
  Pin Default 0x01cbe030: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = White
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x25 0x0b

**amixer**
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 27 [87%] [6.00dB] [on]
  Front Right: Playback 27 [87%] [6.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [-6.00dB] [off]
  Front Right: Playback 19 [61%] [-6.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'


/Cheers

---

### Post by nicfagn on 2007-10-11
What iMac model do you have? The 24'' inch one or another?

---

### Post by nicfagn on 2007-10-11
You can try with this new patch.

---

### Post by Askrates on 2007-10-11
Thanks for the new patch! Unfortunately it doesn't patch properly. I get a:
patching file patch_realtek.c
patch: **** malformed patch at line 101:     
"trying auto-probe from BIOS...\n");

I am using the 20' aluminium imac

A.

---

### Post by cyberdork33 on 2007-10-11
> **nicfagn said:**
> What iMac model do you have? The 24'' inch one or another?

nicfagn, his is one of the new aluminum iMacs that have different hardware than the older 24" iMac that you got the sound patch for before.

---

### Post by nicfagn on 2007-10-11
Sorry, the patch was malformed, so I re-uploaded a hopefully correct version in the previous post.

@ cyberdork33 
Yes, it is the mid 2007 iMac 20'' and has a different subsystem id and pin configuration compared to my late 2006 iMac 24'', but the audio codec chip is the same so I had to do only minor adjustments to make it (hopefully ;)) work.

---

### Post by cyberdork33 on 2007-10-11
> **nicfagn said:**
> @ cyberdork33 
Yes, it is the mid 2007 iMac 20'' and has a different subsystem id and pin configuration compared to my late 2006 iMac 24'', but the audio codec chip is the same so I had to do only minor adjustments to make it (hopefully ;)) work.

Just making sure there was no confusion :)

---

### Post by nicfagn on 2007-10-11
> **cyberdork33 said:**
> Just making sure there was no confusion :)

Thanks, I hope there isn't too much...;)

---

### Post by Askrates on 2007-10-11
No confusion here, though. I have sound :guitar:

I hope there is a chance of getting the patch submitted to the Gutsy developers so that other people than me can benefit from it.

Anyway, thanks again for all your help!

---

### Post by Carl Petersen on 2007-10-11
> **nicfagn said:**
> You can try with this new patch.
Thanks for your patch. Trying it out now.

Works great, thanks again...

---

### Post by clayboy on 2007-10-12
is there anyway you guys could give me a step by step on how to do the patch and everything cause im going crazy ive reboot about over 200 times in the past 3 days i just want to hear something dammit i feel like a deaf man....... thanks.:confused:

---

### Post by clayboy on 2007-10-12
my mac is
24"
2.8ghz
4gb ram
1tb hdd

---

### Post by Askrates on 2007-10-12
clayboy, if your imac is one of the new aluminum ones launched this year you should be able to get sound using the instructions on page 1 of this post. Don't forget to do a software update first.

Btw, was using Ubuntu Gutsy when I got it working. If you are using an older version, your mileage may vary.

---

### Post by clayboy on 2007-10-12
for some reason it wont allow me to do the patch
what should i be typing in to apply the patch i "cd" to the dir and tried typing "patch < alsa-1.0.14-patch_realtek-imac24_v2.2.txt" then it tells me no such file directory and just so you know im using Feisty Fawn at the moment. They should be similar

---

### Post by Askrates on 2007-10-12
After you have downloaded and unpacked the alsa-driver-1.0.14.tar.bz2 file, you browse to the folder **alsa-driver-1.0.14/alsa-kernel/pci/hda** and copy in the alsa-1.0.14-patch_realtek-imac24_v2-2.txt patch.

Then you open the terminal and cd to the **(place-you-have-unpacked-the-driver)/alsa-driver-1.0.14/alsa-kernel/pci/hda directory**. There you can run the command _patch < alsa-1.0.14-patch_realtek-imac24_v2-2.txt_ 

Hope this helps!

---

### Post by clayboy on 2007-10-12
Sweet Jesus i hear sound glorious sound woooooooooooooooooooooooooooooooooooooooooooooooooooooohhhhh thanks guy much much thanks:):):):):):):):)

---

### Post by Askrates on 2007-10-12
:)

---

### Post by cyberdork33 on 2007-10-12
Well, that's two confirmed instances of the patch working. Maybe we can get this integrated as a gutsy update.

---

### Post by nicfagn on 2007-10-12
Oh well, it seems that while I was sleeping something happened :)

It would be very helpful now if the ones for which the patch worked could confirm that:

- speakers are working (this is obvious)
- headphones are working
- microphone is working
- muting/unmuting of the speakers happens on headphones jack insertion/removal

Knowing that, I can proceed to adapt the patch to alsa-1.0.15.RC3 (with sound powersave and working after a resume) and after testing submit it to alsa.

---

### Post by nicfagn on 2007-10-12
Automuting doesn't work with the previous patch, so I made a new one to fix it.

Cheers

---

### Post by FunkyM on 2007-10-14
Despite I am using openSUSE 10.3, using the latest patch (had to manually adjust it as openSUSE already has the iMac24v1 patch included) everything seems to work. Thanks :)

Now I am just missing to control that burning screen brightness...

---

### Post by nicfagn on 2007-10-14
> **FunkyM said:**
> Despite I am using openSUSE 10.3, using the latest patch (had to manually adjust it as openSUSE already has the iMac24v1 patch included) everything seems to work. Thanks :)

Now I am just missing to control that burning screen brightness...

Great :)
Are you using a 20'' or 24'' silver iMac?
Not to be picky but I need to know what you mean with everything:

- Speakers ?
- Headphones ?
- Microphone ?
- Speakers automuting ?

Thanks

---

### Post by FunkyM on 2007-10-15
Ok tested it all now.

iMac 24" Aluminium (DMI iMac7,1)

- Speakers ?
Yes, can hear and control sound.

- Headphones ?
No sound.

- Microphone ?
Not working even with headphones in/out.

- Speakers automuting ?
Yes, speakers mute on plugin in headphones.

As usual I tried to to be mad and clicked all kind of options in the volume control panel when testing each feature.

---

### Post by nicfagn on 2007-10-16
> **FunkyM said:**
> Ok tested it all now.

iMac 24" Aluminium (DMI iMac7,1)

- Speakers ?
Yes, can hear and control sound.

- Headphones ?
No sound.

- Microphone ?
Not working even with headphones in/out.

- Speakers automuting ?
Yes, speakers mute on plugin in headphones.

As usual I tried to to be mad and clicked all kind of options in the volume control panel when testing each feature.

First of all, thanks for your exhaustive reply.

Unfortunately I don't have the new iMac models to test directly, and the patch I made is  based only on what I learned from doing the same for my model, so it is perfectly possible that I missed something or that Apple decided to do something differently.
This is to say that I'm not sure to find a way to make everything work, but if someone has the patience to test the patch for me, we can surely try.

For microphone I had to raise the **first capture channel** volume and set the **first input source** to **Front mic** in the mixer (the gnome one or alsamixer).

Can you post the current output of:

- cat /proc/asound/card0/codec#0
- amixer

---

### Post by FunkyM on 2007-10-16
> - cat /proc/asound/card0/codec#0
- amixer

... output attached.

> For microphone I had to raise the first capture channel volume and set the first input source to Front mic in the mixer (the gnome one or alsamixer).

That does not make the microphone work.

---

### Post by FunkyM on 2007-10-18
@nicfagn: If you could roughly explain to me what you are doing in the patch (afaik you set some pin configuration?) I might test around a couple of values and try to make it wok.

---

### Post by nicfagn on 2007-10-18
> **FunkyM said:**
> @nicfagn: If you could roughly explain to me what you are doing in the patch (afaik you set some pin configuration?) I might test around a couple of values and try to make it wok.

Glad you asked. :)
In fact I cannot see anything useful in the posted data to make the headphones and microphone work.

This block of code in the patch sets up a simple mixer consisting of a volume control and a mute control bound to the 0x0c node that is a sum mixer:
```

static struct snd_kcontrol_new alc885_imac24_v2_mixer[] = {
	HDA_CODEC_VOLUME("Master Playback Volume", 0x0c, 0x00, HDA_OUTPUT),
	HDA_CODEC_MUTE("Master Playback Switch", 0x0c, 0x00, HDA_INPUT),
	{ } /* end */
};

```
The following code configures other nodes to manage speakers, headphones and microphone and connects them with the mixer node.
```

/* iMac 24 Mid 2007 init verbs. */
static struct hda_verb alc885_imac24_v2_init_verbs[] = {
	// Internal speakers: output 0 (0x0c)
	{0x14, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_OUT},
	{0x14, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE},
	{0x14, AC_VERB_SET_CONNECT_SEL, 0x00},
	// Internal speakers: output 0 (0x0c)
	{0x16, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_OUT},
	{0x16, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE},
	{0x16, AC_VERB_SET_CONNECT_SEL, 0x00},
	// Headphone: output 0 (0x0c)
	{0x15, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_HP},
	{0x15, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE},
	{0x15, AC_VERB_SET_CONNECT_SEL, 0x00},
	{0x15, AC_VERB_SET_UNSOLICITED_ENABLE, ALC880_HP_EVENT | AC_USRSP_EN},
	// Front Mic: input vref at 80%
	{0x18, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_VREF80},
	{0x18, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_MUTE},
	{ }
};

```
This line says that the 0x14 node must be an output node
```
	{0x14, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_OUT},

```
the next line says that the output amplifier of the 0x14 node must be unmuted 
```
	{0x14, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE},

```
and this one says that the connection with index 0 must be selected as input (0=0x0c, 1=0x0d, 2=0x0e, 30x0f, 4=0x26)
```
	{0x14, AC_VERB_SET_CONNECT_SEL, 0x00},

```

I choose to use 0x14 and 0x16 as speakers, 0x15 as headphones and 0x18 as microphone looking at their 'Pin Default' lines in the output of 'cat /proc/asound/card0/codec#0'. In fact doing so on my hardware works fine.

If I had a machine to test on I would adopt a brute force approach, commenting everything in the init verbs section except the headphone setup:
```

/* iMac 24 Mid 2007 init verbs. */
static struct hda_verb alc885_imac24_v2_init_verbs[] = {
	// Internal speakers: output 0 (0x0c)
//	{0x14, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_OUT},
//	{0x14, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE},
//	{0x14, AC_VERB_SET_CONNECT_SEL, 0x00},
	// Internal speakers: output 0 (0x0c)
//	{0x16, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_OUT},
//	{0x16, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE},
//	{0x16, AC_VERB_SET_CONNECT_SEL, 0x00},
	// Headphone: output 0 (0x0c)
	{0x**NN**, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_HP},
	{0x**NN**, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_UNMUTE},
	{0x**NN**, AC_VERB_SET_CONNECT_SEL, 0x00},
	{0x**NN**, AC_VERB_SET_UNSOLICITED_ENABLE, ALC880_HP_EVENT | AC_USRSP_EN},
	// Front Mic: input vref at 80%
//	{0x18, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_VREF80},
//	{0x18, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_MUTE},
	{ }
};

```
and then I would try to substitute to **NN** a value between 14, 15, 16, 17, 18, 19, 1a, 1b, until I hear something from the headphones (obviously compiling and loading the new module after each substitution :) ).

If you can also read [this]("ftp://202.65.194.211/pc/audio/ALC885_DataSheet_1.1.pdf") to have some more details.

---

### Post by nicfagn on 2007-10-19
I made another patch that uses a different mixer setup. Instead of a Master volume there are a PC Speaker volume and a Headphone Volume.
If anyone feels lucky he can try to apply the patch and see what happens :)

---

### Post by Kotare on 2008-03-08
Could the brute force approach of systematically trialling  numbers in the init verbs section of nicfagn's patch  *alsa-1.0.16.txt* be used to get the microphone working for a 24" aluminium iMac? 
Is there any danger of damaging the microphone using this method?

---

### Post by nicfagn on 2008-03-08
> **Kotare said:**
> Could the brute force approach of systematically trialling  numbers in the init verbs section of nicfagn's patch  *alsa-1.0.16.txt* be used to get the microphone working for a 24" aluminium iMac?
You can surely try that approach, but the solution could be in a different configuration of pin 0x18.
> Is there any danger of damaging the microphone using this method?
I tried a lot of different configurations on my model before finding a satisfactory one, and had no problems.
I think it's quite safe to do this kind of tests, but I don't have enough knowledge to give you an absolute guarantee.

Bye

---

### Post by cyberdork33 on 2008-03-08
nicfagn, 

It would be much more beneficial if you made patches to the Ubuntu source packages rather than the vanilla alsa source. These could then be submitted with a bug report for quick fix, and also could be used in the mactel-support ppa so that updates can be automatic for those using the ppa.

---

### Post by Kotare on 2008-03-09
nicfagn,
Thank you for your reply.

---

### Post by DirkPP on 2008-03-09
Hello nicfagn & all,

well, my first post here and I just want to thank you for your kind work and contribution for the community members like me - beeing not a total dummy, but without all the tips I've found here, I would have been lost in Linux cyberspace with a silent Mac. 

Oh, our new iMac 20'' wants to say thx, too. Now "he", Gutsy Gibbon,  even talks and sings in Ubuntu. -Your fault". ;-) 

THX

Kind Greetings from Germany
Dirk

---

