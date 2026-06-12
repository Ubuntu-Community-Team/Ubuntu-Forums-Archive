---
title: "Problem installing Ubuntu on Acer Aspire 5040"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by abuzurah on 2007-10-31
The problem is:
I can't install ubuntu (when I click install, it did not show anything)
I am using Ubuntu 7.04 (ship-it)


My computer is an acer aspire 5040 laptop. AMD Turion 64, ATI Radeon Extress 200M, 2-512 Ram, 60 GB hard drive

---

### Post by overdrank on 2007-10-31
> **abuzurah said:**
> The problem is:
I can't install ubuntu (when I click install, it did not show anything)
I am using Ubuntu 7.04 (ship-it)


My computer is an acer aspire 5040 laptop. AMD Turion 64, ATI Radeon Extress 200M, 2-512 Ram, 60 GB hard drive

Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash before the -- then press enter. this will allow you to see any errors.

---

### Post by abuzurah on 2007-11-01
> **overdrank said:**
> Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash before the -- then press enter. this will allow you to see any errors.

Thanks for reply,
but it did't work, just the blank box appear.

---

### Post by overdrank on 2007-11-01
> **abuzurah said:**
> Thanks for reply,
but it did't work, just the blank box appear.

Ok if you don't mind try to start in safe graphics mode and use the F6 remove the quiet splash again and add noapic in its place. Hope the works, good luck!

---

### Post by paul.matthijsse on 2007-11-01
also try as boot argument:
linux irqpoll noapic acpi=off

sometimes that seems to be a solution...

---

### Post by dward526 on 2007-11-01
If possible, try obtaining a copy of the alternate install, it has often worked for me when the graphical install fails.

---

