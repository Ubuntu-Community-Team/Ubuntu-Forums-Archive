---
title: "[SOLVED] MP-BIOS bug: 8254 timer not connected to IO-APIC"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2008-03-07
I get that error every time I boot into gutsy, and it seems to boot up normally without problems after that. I can get rid of the error by adding "noapic" to the kernel line, but what does the error mean?

---

### Post by piratesmack on 2008-03-07
And also, is there any problems that can result from adding "noapic"

---

### Post by counterfactual on 2008-03-07
I'm having the same issue with my MacBook. I've added noapic to the kernel line, and it boots fine for a while, then I start getting the error message again and I have to edit the kernel line again. Why does noapic randomly disappear? This is my first substantial experience with Linux, so I'm pretty clueless.

---

### Post by piratesmack on 2008-03-07
To make it permanent, run this command in a terminal:

sudo gedit /boot/grub/menu.lst


Then locate the kernel line, add noapic, and save

---

### Post by dcstar on 2008-03-07
> **piratesmack said:**
> I get that error every time I boot into gutsy, and it seems to boot up normally without problems after that. I can get rid of the error by adding "noapic" to the kernel line, but what does the error mean?

It means - as has been answered in multiple identical questions - that your BIOS does not fully comply with APIC standards.

In most cases it doesn't matter, and if you use "noapic" you lose all the APIC functionality that actually does work in your hardware.

Just ignore it.

---

### Post by piratesmack on 2008-03-08
> **dcstar said:**
> It means - as has been answered in multiple identical questions - that your BIOS does not fully comply with APIC standards.

In most cases it doesn't matter, and if you use "noapic" you lose all the APIC functionality that actually does work in your hardware.

Just ignore it.

I looked through many similar questions, but none explained it that well. Alright so I guess I'll remove "noapic" from my kernel line and just ignore then error. Thanks :)

---

