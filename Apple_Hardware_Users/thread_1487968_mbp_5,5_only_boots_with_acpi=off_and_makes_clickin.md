---
title: "mbp 5,5 only boots with acpi=off and makes clicking noises"
date: 2010-05-19
forum: Apple Hardware Users
---

### Post by ichigo on 2010-05-19
about ten days ago, i noticed that i still had the karmic version of the mactel repos set in my software sources list and changed that to the lucid version. After that, I've installed a bunch of updates (both mactel and others) which has caused two problems:
[LIST]
[*]My computer gets stuck during boot, if I don't attach the "acpi=off" as a kernel option. If I don't attach it and choose the recovery-mode kernel, the last few lines read:
```
ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 16
forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 16 (level, 
low) ->IRQ 16
ohci1394 0000:04:00.0:  PCI INT A -> Link[Z00J] -> GSI 22 (level, 
low) ->IRQ 22
```
[*]if I use acpi=off, there often is a clicking noise, when I play sound. It get's better/worse when I change the volume and stops, if I pause the playback.
[/LIST]
My computer is a mbp 5,5 with lucid (updated from karmic when lucid became beta) running the pae kernel. I've followed all instructions from mbp community pages...
Any help for one of the two problems is highly appreciated!
Cheers,
ichigo

---

