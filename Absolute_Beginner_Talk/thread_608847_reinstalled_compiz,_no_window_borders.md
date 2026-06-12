---
title: "reinstalled compiz, no window borders"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-11-10
Hey guys, I reinstalled compiz in gutsy, but there are no window borders.

I wanted to install it again, because it used the cpu 100 % when it was running.
Note that in feisty it was workng perfect, with minimal (5-10%) CPU usage.

any ideas?
thanx

---

### Post by creeco on 2007-11-10
did you install the compiz-gnome package?

---

### Post by duruttye on 2007-11-10
Yes, I did.

After a few tries, I managed to make it work, although, it still uses  a lot of CPU.

Thanx anyway.
Another question, do you know how to make the graphics card perform better, on 7.04 glxgears info gave me twice as much FPS.

Thanx

---

### Post by overdrank on 2007-11-10
> **duruttye said:**
> Yes, I did.

After a few tries, I managed to make it work, although, it still uses  a lot of CPU.

Thanx anyway.
Another question, do you know how to make the graphics card perform better, on 7.04 glxgears info gave me twice as much FPS.

Thanx

What is the model of the graphics card?

---

### Post by duruttye on 2007-11-10
It is some kind of Nvidia geforce, maybe 5200 or 7200. I'm not sure.

---

### Post by duruttye on 2007-11-10
Found it, hope it helps.


description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 m

Glxgears info:

4076 frames in 5.0 seconds = 814.614 FPS
4088 frames in 5.0 seconds = 817.551 FPS
4074 frames in 5.0 seconds = 814.772 FPS
3798 frames in 5.2 seconds = 728.433 FPS

I have 1200 mhz processor, 640 ram and 128 ram of the graphics card.

Thanx

---

### Post by DutyDuty on 2007-11-10
Try ```
compiz --replace
emerald --replace
```

---

