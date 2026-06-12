---
title: "Generic kernel: P4 HT shows as two CPUs, yet hyperthreading is disabled"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Tezcatlipoca on 2006-12-06
I'm using Ubuntu 6.10, with the default "Generic" kernel, on a PC with a Pentium 4 3GHz with HyperThreading.


If I check my logs, it says that hyperthreading is disabled.

[from what I've just read, hyperthreading is deliberately disabled by default, because of some security flaw (which is more risky to servers than desktops?).]


But if I check my cpuinfo, it still shows two CPUs, & if I look at the System Monitor, it shows two CPUs.


So how come, if HT is disabled, it still shows up two CPUs? :???: 


If I change my grub to enable hyperthreading (ht=on?), will it actually make much of a difference, if the system already thinks there are two CPUs?

---

### Post by Tezcatlipoca on 2006-12-08
Anyone?

---

