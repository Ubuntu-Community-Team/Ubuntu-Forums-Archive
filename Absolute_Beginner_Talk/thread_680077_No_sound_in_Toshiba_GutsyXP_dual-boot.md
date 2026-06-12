---
title: "No sound in Toshiba Gutsy/XP dual-boot"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Shay Andrews on 2008-01-27
I have a Toshiba Satellite M45-S2652 running a dual-boot of XP and Gutsy. My sound works fine in XP, but not at all in Ubuntu. I've checked alsamixer, and tried to follow [this thread]("http://ubuntuforums.org/showthread.php?t=205449"), but I'm not sure if I can find my sound card's ALSA driver. Here's my output from the first two steps:
```
shay@shay-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [Intel ICH6 Modem], device 0: Intel ICH - Modem [Intel ICH6 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
shay@shay-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at e000 [size=8]
        Memory at a0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0080000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: cc000000-cfffffff
        Prefetchable memory behind bridge: 000000009c000000-000000009fffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000bfff
        Memory behind bridge: c8000000-cbffffff
        Prefetchable memory behind bridge: 0000000098000000-000000009bffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1200 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1220 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1240 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1260 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at f4000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: b8000000-c7ffffff
        Prefetchable memory behind bridge: 0000000088000000-0000000097ffffff
        Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at e100 [size=256]
        I/O ports at e200 [size=64]
        Memory at d0180000 (32-bit, non-prefetchable) [size=512]
        Memory at d0180200 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at e300 [size=256]
        I/O ports at e400 [size=128]
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1100 [size=16]
        Capabilities: <access denied>

01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
        Subsystem: Toshiba America Info Systems Marvell 88E8036 Fast Ethernet Controller (Inventec)
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at cc000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at c000 [size=256]
        Capabilities: <access denied>

05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2741
        Flags: bus master, medium devsel, latency 128, IRQ 11
        Memory at b800b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at b8001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: bc000000-bffff000
        I/O window 0: 00008000-000080ff
        I/O window 1: 00008400-000084ff
        16-bit legacy interface ports at 0001

05:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 11
        Memory at b8000000 (32-bit, non-prefetchable) [size=2K]
        Memory at b8004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

05:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 5
        Memory at b8008000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

05:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 11
        Memory at b800a000 (32-bit, non-prefetchable) [size=256]
        Memory at b800a100 (32-bit, non-prefetchable) [size=256]
        Memory at b800a200 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```
What should I do next?

---

### Post by Furat on 2008-01-28
Did u checked the mixer and there is nothing mute ?? 
did u tried  to use a headphone ?

---

### Post by Shay Andrews on 2008-01-28
Yes, and yes.

---

### Post by ehsan1983ca on 2008-03-28
Hey guys,
I'm having the same problem, but for me I used to have version 7.04 first and everything was fine except internet connection. By runnung the live version of 7.10 I was able to hear the drum sounds at the log in screen and also internet was working. Now after the HD-installation, there is no sound. I tried the **alsamixer** but no channel was labeled IEC and I made all of them unmute to check if anything will change. 
No sound till now...
my laptop hardware are as follow:

The laptop is a Toshiba Satellite M45-S265
 System Characteristics:
-TOSHIBA® Express Media Player for quick access to CD, DVD
-Switch: Power, Wireless Communication
-Mobile Intel 915GM Express Chipset
-Intel PRO/Wireless 2200BG (802.11b/g)
-Analog Devices, Inc. AD1981B Software Sound, AC'97 Rev2.2
-Direct 3D Sound; DirectSound, Direct Music, MIDI (playback)
-Intel® Graphics Media Accelerator 900, 10-128MB Internal

complete system specs can be found at: (the only difference being that I have 1 gig of ram vs. the 512 stated and I'm running Ubuntu instead of Windows. ;-) )
[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_outFrm.jsp?moid=1042090&rpn=PSM40U&ct=DS&soid=1094376&BV_SessionID=@@@@0293416549.1205213019@@@@&BV_EngineID=ccceadedidhiedlcgfkceghdgngdgmn.0](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_outFrm.jsp?moid=1042090&rpn=PSM40U&ct=DS&soid=1094376&BV_SessionID=@@@@0293416549.1205213019@@@@&BV_EngineID=ccceadedidhiedlcgfkceghdgngdgmn.0)

please help me with detail, I am a little bit stranger to the Linux environemnt. 
Thank you in advance...

---

