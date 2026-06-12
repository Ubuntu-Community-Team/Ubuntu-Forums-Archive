---
title: "sound blaster Live! problems"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-09
I am only getting sound from the front left speaker of my 5.1 system.

I ran:
```
speaker-test -Dplug:surround51 -c6 -twav
```
to confirm this and all I hear is front left.

Any ideas?

```
cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SBLive 5.1 [SB0060]
                      SBLive 5.1 [SB0060] (rev.7, serial:0x80611102) at 0x1100, irq 21
```

---

### Post by Mramius on 2007-12-09
Shameless bump

---

