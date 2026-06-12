---
title: "Screen Resolution Without monitor plugged in"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by dmalopsy on 2005-09-03
Is there a way to force X to boot with a specified resolution when there is no monitor plugged in at bootup. Cos it defaults to 640x480 if my monitor is not plugged in. If the monitor is plugged in, it will go to any resolution i want. I have tried moding the conf file, but it dont help :(

---

### Post by dmalopsy on 2005-09-03
ah figured it out, i just booted the machine normally without the monitor, and than did a package reconfigure on xorg package and set the resolution manully to the one i wanted.

---

