---
title: "Ubuntu keeps hanging suddenly"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by markcls on 2007-03-15
My Ubuntu keeps hanging all of sudden. Sometimes my comp can run for hours without the dreadful hang, sometimes after a few minutes. Is there any way to diagnose this problem? Like, some log file or something that I can check?

System Specs:
Pentium 4 2.4C HT
Abit IS-7
Powercolor ATI Radeon 9700
2*256 PC3200 Mushkin BlueLine DDR
120GB Maxtor Hard Drive
Sound Blaster Audigy DE

Software:
ATI Proprietary Drivers
Beryl + XGL (Ubuntu used to hang even without Beryl and XGL)
Kernel: 2.6.17-11-generic

---

### Post by lamalex on 2007-03-15
what version ati drivers do you have? with older version ATi drivers I had lockups, the newest drivers fixed it for me.

---

### Post by Kobalt on 2007-03-15
Is your hard drive a SATA drive ?

---

### Post by markcls on 2007-03-15
I have the latest drivers for ATI. But I remember my computer hanging even before I installed those ATI drivers.

And yes, I'm using a SATA drive :)

---

### Post by Kobalt on 2007-03-15
Then I guess that could be the SATA controller. I've been experiencing the same problems with the 2.6.20-8 kernel in Feisty. Since  2.6.20-9 and now  2.6.20-10, it's fine.
You should try to search the [Launchpad]("http://launchpad.net/ubuntu") for bugs with your hardware, see if any solution has been offered.

---

