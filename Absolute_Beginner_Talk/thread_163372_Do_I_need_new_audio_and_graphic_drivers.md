---
title: "Do I need new audio and graphic drivers?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by gardara on 2006-04-20
I'm on a hp compaq nx9005. 
The drivers I currently have are those I got when I installed dapper.
I think I need new audio driver for my laptop, the sound works now but is terrible and sounds like some very very low samplerate... do I need a new driver or can I config something?

I also think I need a new graphics driver because the graphics in games and stuff is not so good... or is it maby the best I can get on a nx9005 laptop?

---

### Post by netkid91 on 2006-04-20
Post the output of "lspci" and "lspci -v" please.

---

### Post by gardara on 2006-04-20
ah yes sorry.

lspci
```
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
0000:00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
0000:00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```

lspci -v
```

0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Memory at d0500000 (32-bit, prefetchable) [size=4K]
        I/O ports at 8090 [disabled] [size=4]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin USB
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Audio
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 8400 [size=256]
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
        Subsystem: ALi Corporation ALI M1533 Aladdin IV ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Modem Device
        Flags: medium devsel, IRQ 3
        Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8800 [size=256]
        Capabilities: <available only to root>

0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Unknown device 6933:0002
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 80000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10000000-11fff000 (prefetchable)
        Memory window 1: 12000000-13fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

0000:00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Unknown device 6933:0002
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at d0008000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 14000000-15fff000 (prefetchable)
        Memory window 1: 16000000-17fff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

0000:00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at d0009000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if b0)
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin IDE
        Flags: bus master, medium devsel, latency 32
        I/O ports at 8080 [size=16]
        Capabilities: <available only to root>

0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Hewlett-Packard Company Pavilion ze4400
        Flags: medium devsel

0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network
        Flags: bus master, medium devsel, latency 90, IRQ 11
        I/O ports at 8c00 [size=256]
        Memory at d000a000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 18000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Video
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at 12000000 (32-bit, non-prefetchable) [size=64K]
        Memory at 12010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

```

---

### Post by netkid91 on 2006-04-20
Not sure about the audo right yet...but it look's like (for games and stuff) you need the (proprietary) ATI fglrx driver.  I gotta reboot to finish an update, I'll give you some more info when I finish.

---

### Post by gardara on 2006-04-20
ok great! I'll be waiting for your instructions :)

---

### Post by netkid91 on 2006-04-20
Aha got [linkage]("http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fglrx") for you, I have a ATI R9200 and this'll help me out to, hope it helps.

---

### Post by gardara on 2006-04-20
ok great, I'll try the link, but what about the audio?

---

### Post by netkid91 on 2006-04-20
I don't know about the audio, the forum search is your greatest tool, try searching around for stuff concerning your sound card.

---

### Post by nemixer on 2006-05-30
Hallo,

I have the same sound card (on hp laptop) and I am running an updated Dapper,
same problem with the sound. It works, but it sounds very bad, much worse than with Breezy.
I didn't find anything on the forum.. I am still asking my big friend google.
If I find something I'll post it.

bye

---

