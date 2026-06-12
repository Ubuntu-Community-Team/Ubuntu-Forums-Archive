---
title: "Can't add USB printer on Dual G5"
date: 2006-06-08
forum: Apple PPC Users
---

### Post by tidris on 2006-06-08
I have an HP Deskjet 990Cse printer with USB interface. 

I connect it to the dual G5 and try to add a printer via the GUI (System -> Administration -> Printing). The printer doesn't show up in the "Step 1 of 3: Printer Connection" screen ("no printers detected" it says). If I continue regardless of that, I am able to add a printer but nothing happens when I try to print to it.

This problem doesn't happen on my Pismo G3 powerbook. In there the USB printer shows up on the "Step 1 of 3: Printer Connection" screen and I am able to print to it after the printer is added.

Both computers are running 6.06 LTS installed from the live desktop CD.
I verified that hplip, cups, foomatic are installed in both computers.

Any ideas on how to work around this problem?
Is anybody else having problems with USB printers on G5 hardware?

---

### Post by swartzfeger on 2006-06-08
[QUOTE=tidris]Is anybody else having problems with USB printers on G5 hardware?[/QUOTE]

Same issue -- installed and booted 6.06 last night, played around a bit, then when to add my USB Samsung ML-2010 laser printer. Didn't recognize it.

---

### Post by colinhayes on 2006-06-08
after attempting to add my hp laserjet 1300 last night, I discovered that I'm in the same rut

---

### Post by tidris on 2006-06-09
My problem is fixed after upgrading hplip to version 0.9.11 which is available here:

[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)

---

