---
title: "No sound"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-09-14
Hi, I have somehow lost my sound. I did edit the startup recently but I have checked and alsa is on already, any ideas what I might have lost? My sound card default in ubuntu is set to ATI IXP and i'm sure thats what it was set on, I also think it may have something to do with on bootup I get postfix configuration failed, how do I fix this?

Calv

---

### Post by calvinthomas on 2006-09-14
A bit of an update: I ran Multimedia Systems Selector from the preferences menu and in there I have AlSA, OSS, Test, Custom and silence. Testing the sound in any of them doesn't give me any sounds. Strange thing is it was working previously, its just suddenly stopped!

Calv

---

### Post by calvinthomas on 2006-09-14
bump and some info, i'm frustrated with this one because it was working! Grrrr! Ok here is some info, please help me!

**Input from aplay -l**

calvin@calvin-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**Input from lspci -v**

calvin@calvin-laptop:~$ lspci -v
0000:00:00.0 Host bridge: ATI Technologies Inc ATI Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
        Flags: bus master, 66MHz, medium devsel, latency 64

0000:00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: c8000000-cfffffff
        Capabilities: <available only to root>

0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: c0200000-c02fffff
        Capabilities: <available only to root>

0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 225
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8410 [size=16]
        Capabilities: <available only to root>

0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c0300000-c03fffff
        Prefetchable memory behind bridge: 30000000-31ffffff

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 217
        Memory at c0003400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 217
        Memory at c0003800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at c0200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: AMBIT Microsystem Corp. Aspire 3022WLMi
        Flags: bus master, fast devsel, latency 64, IRQ 177
        Memory at c0304000 (32-bit, non-prefetchable) [size=8K]

0000:06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at c0308000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 32000000-33fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

0000:06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at c0309000 (32-bit, non-prefetchable) [size=2K]
        Memory at c0300000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Acer Incorporated [ALI]: Unknown device 007e
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0306000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

**Input from modprobe snd-**

calvin@calvin-laptop:~$ sudo modprobe snd-
FATAL: Module snd_ not found.
[B]

Calv

---

### Post by xpod on 2006-09-14
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Might help.....lost mine for no reason on occasion too.
I ended up trying the oss lot ...that helped moi

---

### Post by calvinthomas on 2006-09-14
Fixed! Have no idea what actually fixed it but its started working again, thanks for the suggestion xpod, if I have the problem again i'll try it!

Calv

---

### Post by xpod on 2006-09-14
> Have no idea what actually fixed it but its started working again,

Exactly how i do things......:-\"

---

### Post by adds2one on 2006-09-17
I lost my sound in the last few days too. The only thing that changed on my system is that I allowed synaptic to install the recent kernel updates. A lot of people had a lot of trouble with these updates, some to do with sound.

Here is my post [http://ubuntuforums.org/showthread.php?t=259436](http://ubuntuforums.org/showthread.php?t=259436)

---

### Post by marianomd on 2007-06-07
I also have ATI IXP AC97 and **solved it this way**:

1) Open the mixer in gnome.
2) Check that the selected device is **ATI IXP (Alsa mixer)**
3) Open preferences dialog and check **External Amplifier** (last in my list)
4) Close this dialog and go to the "Switches" tab (I have it in spanish as "conmutadores" so I suppose it's translated as switches)
5) Check (enable) the external amplifier.

That's all. No need to reboot. 

Cheers

---

