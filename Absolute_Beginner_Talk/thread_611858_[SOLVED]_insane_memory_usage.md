---
title: "[SOLVED] insane memory usage"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-13
usually i run everything on 250mb of ram and no swap, not even 1 btye.

now im running 600mb RAM and 330mb swap?

thats more then i use in windows..

TOP says:

Mem:   1033908k total,  1018764k used,    15144k free,    18732k buffers
Swap:  2698912k total,   362912k used,  2336000k free,   309988k cached

although system monitor says my largest ram usage is 88mb :S

waht could be causing it?

---

### Post by solar george on 2007-11-13
You do know that Linux caches closed programs in memory to speed up opening them later.

---

### Post by CatKiller on 2007-11-13
Not just closed programs. Every file that gets loaded into memory stays there until the memory gets used for something else.

Empty memory is wasted memory.

---

### Post by Inxsible on 2007-11-13
you need to subtract the "cached" or "buffered" size from "used" size, to see the actual usage.

---

### Post by skymera on 2007-11-13
funny thing i got swappiness on 0 and ive only had 2 programs open.

amsn and swiftfox.

---

### Post by CatKiller on 2007-11-13
> **skymera said:**
> ive only had 2 programs open.

amsn and swiftfox.

...and the kernel, and X, and your printer driver, graphics driver, desktop environment...

Empty memory **is** wasted memory. You might need to access those files any time now. :)

---

### Post by skymera on 2007-11-13
ok restarted, got the same progs open, 230mb RAM uage, and0 bytes swap.

weird =S

oh well, seems fine now.

---

