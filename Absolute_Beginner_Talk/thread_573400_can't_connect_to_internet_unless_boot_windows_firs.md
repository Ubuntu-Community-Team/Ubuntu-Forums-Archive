---
title: "can't connect to internet unless boot windows first"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-10-11
ok...this is weird.

If i turn on my computer and go directly to linux, my wireless card light doesn't work, and i can't connect to the internet.
I i go first to windows, let the wireless connect, and then go to linux, it works.

can someone help me understand what's going on, and how to solve it?

---

### Post by Pulka on 2007-10-11
it's the last thing i need to drop windows for good. Please!!!!

---

### Post by Daveth on 2007-10-11
I think folk here need to know a bit more detail. Have you explored the topics in

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

. It would also help to post the output in a terminal of 

```
lspci  -v
```

so we know what chip we are trying to drive. Which version of ubuntu are you using as well?

---

### Post by handydan918 on 2007-10-11
You might try shutting windows all the way down (not a reboot) and leaving it off for 5-10 seconds, then boot into Linux and see if your card is properly initialized. 
With some cards, Windows doesn't kill the card on a reboot, and Linux fails to re-initialize the card on boot. 
Just a thought...

---

### Post by Pulka on 2007-10-12
> **Daveth said:**
> I think folk here need to know a bit more detail. Have you explored the topics in

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

. It would also help to post the output in a terminal of 

```
lspci  -v
```

so we know what chip we are trying to drive. Which version of ubuntu are you using as well?


Be aware that this result is conditioned to the fact that right now i have the card working. Again, had to boot first windows, then linux

:~$ lspci  -v
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0, IRQ 6
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e05fffff
        Prefetchable memory behind bridge: 30000000-35ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]
        Memory at 36000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: medium devsel, IRQ 10
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, fast devsel, latency 64, IRQ 6
        Memory at e0204000 (32-bit, non-prefetchable) [size=8K]
        [virtual] Expansion ROM at 34000000 [disabled] [size=16K]
        Capabilities: <access denied>

02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0305
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at 3800 [size=32]
        Memory at e020a000 (32-bit, non-prefetchable) [size=32]
        Memory at e0209000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at e0208000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0209800 (32-bit, non-prefetchable) [size=2K]
        Memory at e0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0064
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0206000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

---

### Post by Pulka on 2007-10-12
> **handydan918 said:**
> You might try shutting windows all the way down (not a reboot) and leaving it off for 5-10 seconds, then boot into Linux and see if your card is properly initialized. 
With some cards, Windows doesn't kill the card on a reboot, and Linux fails to re-initialize the card on boot. 
Just a thought...

that's exactly what happens. If i reboot, linux manages to initiialize the card. But if a completly shut down the computer for 1 minute, linux fails to re-initialize the card.

---

### Post by Pulka on 2007-10-12
what can i do to fix this?

---

### Post by jgrabham on 2007-10-12
A possible explanation, is that Windows installs sets up the firmware, but Ubuntu cant, but the firmware stays after you reboot.  Not a lot you can do about that really.

---

