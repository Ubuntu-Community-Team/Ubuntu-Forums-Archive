---
title: "Kubuntu 7.10 - no sound on Toshiba Satellite P105-S6197"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by prodigy_ on 2008-03-05
Please, don't consider me lazy or impatient. I know it's a common problem. I've made quite a research on this topic. I'm aware of DSDT errors in P105 BIOS. 

But the problem is that people are suggesting different things, and most of them I've already tried to no avail with the exception of manual DSDT editing (I'm not much of a coder and I don't feel like I manage it without a detailed step-by-step HOWTO).

---

That's what I have:

BIOS: v.4.20
Kernel: 2.6.22-14-generic
Codec: Conexant CX20549 (Venice)
Sound Driver: 3.8.1a-980706 (ALSA v.1.0.15rc3 emulation code)

(lspci)
```
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems AC97 Data Fax SoftModem with SmartCP
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

(modinfo soundcore)
```
filename:       /lib/modules/2.6.22-14-generic/updates/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:
vermagic:       2.6.22-14-generic SMP mod_unload 586
```

---

I was told that for Ubuntu I don't need to patch/recompile kernel and DSDT editing is enough. Is that true? Anyway, if anyone has working and compatible DSDT.aml (or another solution) it will be greatly appreciated.

---

### Post by prodigy_ on 2008-03-05
No suggestions? Nothing a newbie could use? Well, considering this a well-known and (supposedly) resolved problem, that's kind of sad...

---

### Post by prodigy_ on 2008-03-05
Ok, I found a guide myself and followed its instructions. It all worked like a charm... except that after reboot I had just as much sound as before. I suppose that a grand total of 20 hours fruitlessly spent on *one* problem is enough for me.

---

Oh a side note (a bit offtopic but still): I'm not such a beginner. I have some 15 years of IT experience, including strictly command-line BSD servers. But servers usually don't have audio, you see. Besides, when it's your job, you get paid for your efforts. When it your home PC though, you expect it to work and problems, should they arise, to be solvable in a timely manner. Unfortunately, Linux (even Ubuntu) fails miserably in this respect. 

It was like this 10 years ago when I first tried RedHat (ironically it was v.7.10 too) and nothing has changed ever since. Well, not exactly nothing... for sure KDE looks much nicer now. But Linux still lacks functionality out-of-the-box. Yes, audio is basic functionality for any home PC (and I don't ask for complicated things like WiFi or SD card-reader support).

---

They say the third time is lucky. Maybe, but for now I'm back to Vista. Sure, it's poorly designed and resource hungry but it works and Linux doesn't. See you in 10 years.

---

### Post by tempestivo on 2008-03-14
Finally got sound (and fan!) to work using Hardy Heron Alpha 6. Unfortunately it still isn't playing out of the headphone jack (which is actually what I use most).

---

