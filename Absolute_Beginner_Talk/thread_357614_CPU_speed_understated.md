---
title: "CPU speed understated"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by duncan_nz on 2007-02-09
Hi all,

I am running Ubuntu 6.10, and when I have run programs such as the transgaming Cedega setup wizard for example, it always understates my cpu.

I have a AMD 64 3700 cpu, which runs at a clock speed of 2.1 or 2.2 ghz, but whenever I check it on the setup wizard for example it auto detects it as only being a 1.0ghz cpu.

Is Linux somehow only running my cpu at 1.0 ghz, or is it picking it up as 1.0ghz but running it at 2.1-2.2 ghz like it should?

Other than this, I'm really enjoying my Linux experience, and if it were not for a few games that pretty much only work in windows I would be running a pure linux setup instead of a duel boot system.:)

---

### Post by neilp85 on 2007-02-09
Try doing some CPU intensive tasks and you should see it crank up to it's full speed, otherwise it will be scaled down as a power saving measure.

---

### Post by igknighted on 2007-02-09
> **neilp85 said:**
> Try doing some CPU intensive tasks and you should see it crank up to it's full speed, otherwise it will be scaled down as a power saving measure.

Hmm, I use KDE, but in KDE there is an icon for the kpowersave daemon in the systray, which I can adjust my settings at.  Try turning the CPU setting to performance with gnome's equivalent and running Cedega's detect function again, it should recognize it better.  I wouldn't worry about it too much though unless your performance w/ Cedega is poor.

---

### Post by duncan_nz on 2007-02-10
> **igknighted said:**
> Hmm, I use KDE, but in KDE there is an icon for the kpowersave daemon in the systray, which I can adjust my settings at.  Try turning the CPU setting to performance with gnome's equivalent and running Cedega's detect function again, it should recognize it better.  I wouldn't worry about it too much though unless your performance w/ Cedega is poor.

I also forgot to mention that doom3, picked it up as being 1.0 ghz also and so set the game settings to low also, and other games I play such as dod source may not perform as well.

I would like to know how to turn the cpu power saving function off!!!

---

### Post by neilp85 on 2007-02-11
> **duncan_nz said:**
> I would like to know how to turn the cpu power saving function off!!!

Unless you have the correct options compiled in your kernel, it's not going to be possible to do manual processor frequency scaling.

---

### Post by Hubris2 on 2007-02-14
Check your bios settings....I have the same processor and the system boots at 1000Mhz....but with the correct bios setting - it scales up to 2.2 properly when I run a benchmark.

---

