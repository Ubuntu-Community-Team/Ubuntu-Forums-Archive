---
title: "Boot options"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2008-03-18
I've been wrestling with this for a few months now (search my user name) and here's my problem. I'm tring to install 7.10 on my sister's new Compaq Presario with
AMD Athlon 64 X2 Dual-Core Mobile Technology TK-55; 1.8GHz
1024MB DDR2 SDRAM
Nvidia GeForce Go 6100 (UMA) with up to 288MB total available graphics memory and
Up to 1600MHz system bus running at AC/DC Mode 35 watt, Laptop. It hangs when trying to load the hardware drivers. It used to say the buffer was full when trying to load the drivers and it used to fade to white.

Now I can get into the system with the latest puppy linux. What should I change to help it boot normally?

---

### Post by rigol on 2008-03-18
Have you tried booting with noapic option? This fixed this issue for me (AMD Athlon X2 too).

---

### Post by deepclutch on 2008-03-18
did u tried **ubuntu alternate cd**?as far as I remember AMD X2 system needs to disable some thing in their BIOS..some "virtual" sorry forgot the term,.research ur BIOS for that term.disable it.

---

### Post by rigol on 2008-03-18
The normal CD runs fine on AMD X2 with noapic boot option - at least on mine.

---

### Post by woodsonoversoul on 2008-03-18
Yay! I'm booting fine now with acpi=off! however I get a warning message about pnpbios and the login sound effect hangs in the background and loops. I turned it off, any other ideas

---

### Post by rigol on 2008-03-18
Weird. Did you actually try and add "noapic" as a boot option? Or what did you do to get acpi=off?

---

