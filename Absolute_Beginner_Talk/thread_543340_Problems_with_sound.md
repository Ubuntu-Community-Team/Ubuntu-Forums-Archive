---
title: "Problems with sound"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by rajvirnijjar on 2007-09-05
Hello,

I am using ubuntu fiesty. I am having problems with the sound, sometimes it works and sometimes it dosent. My sound card is an onboard card. The chipset is from VIA.

---

### Post by iver2435 on 2007-09-05
Hello,

        While you have given some information, I think more information will be needed to solve your problem.  Could you please post the output of the following command:

```
lspci -v
```

Also, does the sound work at boot time, and then after using your computer it goes away, or is it never there from the start?  What kinds of scenarios are you seeing when the sound isn't working?  Is it after opening a specific program or after doing a specific task?

Give us some of your mental notes so we can help troubleshoot.  Thanks!

---

### Post by rajvirnijjar on 2007-09-05
Here is the output

```

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: d8000000-e7ffffff
        Capabilities: <access denied>

00:0b.0 Multimedia audio controller: Rockwell International Unknown device 4310
        Subsystem: Risq Modular Systems, Inc. Unknown device 4310
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at b000 [size=64]
        Capabilities: <access denied>

00:0b.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
        Subsystem: Risq Modular Systems, Inc. Unknown device 4311
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at ea000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

00:0b.2 Input device controller: Rockwell International Unknown device 4312
        Subsystem: Risq Modular Systems, Inc. Unknown device 4312
        Flags: bus master, medium devsel, latency 0
        Memory at ea010000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
        Subsystem: ABIT Computer Corp. KV7
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at b400 [size=8]
        I/O ports at b800 [size=4]
        I/O ports at bc00 [size=8]
        I/O ports at c000 [size=4]
        I/O ports at c400 [size=16]
        I/O ports at c800 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 16
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at cc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at ea011000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: medium devsel, IRQ 19
        I/O ports at e000 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: ABIT Computer Corp. Unknown device 1408
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at e400 [size=256]
        Memory at ea012000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0002
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 21
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at a000 [size=256]
        Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e8000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 0003
        Flags: stepping, 66MHz, medium devsel
        Memory at e0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at e9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

```

When the computer loads and makes a sound at the login screen then the sound works fine but when it dosent make a sound it dosent work. The sound worked on the totem media player even though there was no sound at the startup screen but now that dosent even work. Another example is when it didnt make the initial sound at the login screen then the sound didnt work on youtube and other pages like that but it worked fine offline.

Thanks in advance

---

