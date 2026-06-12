---
title: "TV tuner works in breezy and doesnt work in fesity !"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by medya on 2007-08-19
hey I have a TV Tuner , named ePro .
here is the result of lspci 

> 0000:02:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)


in feisty fawn (latest ubuntu) 
for "dmesg", it says it can not auto detect the tv tuner and I should tell it the card number by myself.

but in breezy live cd (they very very old ubuntu ) it works fine !
and dmesg says :
> [4294884.788000] Linux video capture interface: v1.00
[4294884.949000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4294884.974000] PCI: Enabling device 0000:02:0a.0 (0004 -> 0006)
[4294884.974000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294884.974000] saa7130[0]: found at 0000:02:0a.0, rev: 1, irq: 22, latency: 32, mmio: 0xf2800000
[4294884.974000] saa7130[0]: subsystem: 1131:0000, board: Sabrent SBT-TVFM (saa7130) [card=42,autodetected]
[4294884.974000] saa7130[0]: board init: gpio is 80c000
[4294885.078000] saa7130[0]: Huh, no eeprom present (err=-5)?
[4294885.128000] tuner 0-0060: chip found @ 0xc0 (saa7130[0])
[4294885.128000] tuner 0-0060: type set to 17 (Philips NTSC_M (MK2))
[4294885.259000] saa7130[0]: registered device video0 [v4l2]
[4294885.308000] saa7130[0]: registered device vbi0
[4294885.338000] saa7130[0]: registered device radio0



how I can make the New ubuntu to work like old ubuntu ???

---

