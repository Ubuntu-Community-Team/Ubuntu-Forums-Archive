---
title: "Dual Monitor / Dual Video Card bug"
date: 2006-06-06
forum: Bug Reports / Support
---

### Post by bistros on 2006-06-06
Hi all:

I've tested this problem and done enough analysis to determine there may be a bug in X (Dapper release).

I have taken a working Breezy system that was running two video cards with two monitors and upgraded to Dapper.  On upgrade the dual monitors stopped working.  The motherboard is an ASUS P4P800 with embedded i810 AGP video on board.  I had (at first) an ATI Rage IIC PCI video card installed (later changed to an Nvidia FX5500 PCI).  It doesnt matter what cards are installed, in what priority, but the second card always fails at the same point - loading libint10.so, where there is either a SHMAT problem, or X startup fails to read V_BIOS.  The error is consistent on the second card,regardless of what the second card is.

I can post the X.0.log, dmesg output, lspci output etc. if required.

I have tested all permutations and combinations, with and without Xinerama, with AGP set as primary in BIOS, with PCI ATI set as primary, and finally with PCI Nvidia set as primary.  The monitors are identical Samsung analog LCD panels - SyncMaster 920N.

Each card (i180 embedded), ATI Rage IIC and Nvidia GeForce 5500 all work individually in their own xorg.conf files, the problem only occurs when two them are installed.

--
Bill Strosberg

---

### Post by pebble on 2006-06-06
You aren't using Option "ConnectedMonitor" by any chance are you? That bit me when I upgraded; apparently you should use Option "UseDisplayDevice" now.

---

### Post by bistros on 2006-06-06
No, not using ConnectedMonitor, but I'm not using UseDisplayDevice either .... heading off to read about the option right now ....

---

