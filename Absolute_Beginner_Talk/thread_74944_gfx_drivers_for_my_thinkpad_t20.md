---
title: "gfx drivers for my thinkpad t20"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by whiterabbit on 2005-10-13
After installing Ubuntu on my thinkpad t20, I've been trying to work out which graphics drivers I'll be needing. 

Typing in "lspci" gives...

```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:03.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
0000:00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
```

Typing lspci |grep AGP gives...

```
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
```

No idea where to go from there.. any help would be great.  Please...  I really need it.

---

