---
title: "Sound stopped working"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-02-23
The sound for my laptop doesn't work anywhere. My sound device is a ES1983S Maestro-3i PCI Audio.

When I go to System > Preferences > Sound > and hit test for Maestro in Sound events > Sound playback, I get this error:

```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.
```

Does anyone know what is up and how to fix the problem?

Cheers

---

### Post by Kateikyoushi on 2007-02-23
What's the output of this command ?

```
lspci -v
```

---

### Post by spamzilla on 2007-02-23
Here it is:

> 
matt@matt:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 32
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fd000000-feffffff
        Prefetchable memory behind bridge: f8000000-fbffffff

00:03.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Dell Latitude C600
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 28000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:03.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Dell Latitude C600
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 28001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 24000000-25fff000 (prefetchable)
        Memory window 1: 26000000-27fff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at 0860 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at dce0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
        Subsystem: Dell Latitude C600
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d800 [size=256]
        Memory at f3ffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
        Subsystem: 3Com Corporation Unknown device 6456
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d400 [size=256]
        Memory at f3ffdc00 (32-bit, non-prefetchable) [size=128]
        Memory at f3ffd800 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
        Subsystem: 3Com Corporation Unknown device 615b
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d000 [size=256]
        Memory at f3ffd400 (32-bit, non-prefetchable) [size=256]
        Memory at f3ffd000 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell Latitude C600
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        I/O ports at ec00 [size=256]
        Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
        [virtual] Expansion ROM at fd000000 [disabled] [size=128K]
        Capabilities: <access denied>

06:00.0 Network controller: RaLink Wireless PCI Adapter RT2400 / RT2460
        Subsystem: Accton Technology Corporation Unknown device ee07
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at 26000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>



---

### Post by Kateikyoushi on 2007-02-23
Okay I see your soundcard, another question what is the output of this ?

```
aplay -l
```

---

### Post by spamzilla on 2007-02-23
Here is the output of aplay -l

```
matt@matt:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCI [ESS Maestro3 PCI], device 0: Maestro3 [Maestro3]
  Subdevices: 0/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
```

Thanks so far guys and gals :)

---

### Post by spamzilla on 2007-02-23
It seems only embedded videos on websites have no sound as other sources of sound works ok.

---

### Post by spamzilla on 2007-02-23
bump. anyone any ideas?

---

### Post by Kateikyoushi on 2007-02-23
I did a search about the error and was the same for other like you although they got the error message sound worked. The lack of sound on websites might be because of missing codecs.
Make a search on the forum there are howtos on how to make them work.

Youtube works for me but google videos not, I seldom watch them so does not really bother me.

---

