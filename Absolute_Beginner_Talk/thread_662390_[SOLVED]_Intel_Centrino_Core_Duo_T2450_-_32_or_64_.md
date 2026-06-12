---
title: "[SOLVED] Intel Centrino Core Duo T2450 - 32 or 64 bit?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Novawave on 2008-01-08
[COLOR="Red"]**SOLVED!**[/COLOR]
Thanks for the help guys, now I can install the correct version without freaking out.



**Original Post: **[I]Hey Folks, I am trying to figure out if my Laptop is running on 32 or 64 bit, so I can then download the correct version of Ubuntu.

System Info:

Intel(R) Core(TM) Duo CPU - T2450 @ 2.00GHz
1 GB RAM
Mobile Intel(R) 945 Express Chipset Family

(Regarding the Mobile Intel(R) Chipset, has anyone had experience with it and Ubuntu? Just want to get any problems down before I install Ubuntu)

Laptop Manufacturer: TOSHIBA
Laptop Model: Satellite A200 -AH5

Also, this is a totally noob thing to ask but the sticker on my laptop says "Centrino Duo" not "Core Duo". I am guessing that it does not matter but if anyone has the time could you explain?[/I]

---

### Post by barbedsaber on 2008-01-08
Im pretty sure that the only 64 bit procceser's say amd 64 on the box, I am 99.9999999% sure that that is 32 bit intel cemtrino duo is 32 bit.

---

### Post by p_quarles on 2008-01-08
Core 2 Duo is a 64-bit processor. Core Duo is 32-bit.

To find out which you have, run:
```
sudo lshw
```
Post the output if you need any help interpreting it.

---

### Post by scxtt on 2008-01-08
i have 1 (or 2, depending on how you look @ it) of those ... it's 32-bit.

---

### Post by yaknowwat on 2008-01-08
you dont 'need to sudo lshw to get hardware info.

also i would suggest doing it the easy way and putting the out put of

```
uname -a
```

as all you want to see is basic system info

also processor wise Intel has 64bits for a while since their Core 2 Duo's

Centrino Duo is just the processor class for laptop processors as the architecture between Desktop and Laptop Processors are different ones meant to be fast and efficient the other is meant more to be efficient than fast.

Anyways you are most likely running a 32-bit version for the amount of RAM you have no need to go 64-bit unless you have 3-4GB+ RAM.

---

### Post by p_quarles on 2008-01-08
> **yaknowwat said:**
> you dont 'need to sudo lshw to get hardware info.

also i would suggest doing it the easy way and putting the out put of

```
uname -a
```

as all you want to see is basic system info

also processor wise Intel has 64bits for a while since their Core 2 Duo's

Centrino Duo is just the processor class for laptop processors as the architecture between Desktop and Laptop Processors are different ones meant to be fast and efficient the other is meant more to be efficient than fast.

Anyways you are most likely running a 32-bit version for the amount of RAM you have no need to go 64-bit unless you have 3-4GB+ RAM.
It's true that you don't *need* to run lshw to get the CPU info, but it's the easiest way to get it regardless of the desktop environment. In any case, "uname -a" outputs kernel information, not hardware information.

---

### Post by barbedsaber on 2008-01-08
well now that its all working, can you please mark this thread as solved, info in my sig.

---

