---
title: "Ubuntu friendly video cards?"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Chucky G on 2006-05-14
Is there a list of Ubuntu friendly video cards?

Maybe I can pick one up off Ebay if it's an older card. PCI or AGP.

I have an older Intel board that runs a 450mhz processor, so it can't be too new.

I asked this question in another post, but I think this question could use its own thread.

---

### Post by adam.tropics on 2006-05-14
Checkout[ this]("http://www.linuxcompatible.org/compatlistcat23.html") site

---

### Post by az on 2006-05-14
[QUOTE=Chucky G]Is there a list of Ubuntu friendly video cards?

Maybe I can pick one up off Ebay if it's an older card. PCI or AGP.

I have an older Intel board that runs a 450mhz processor, so it can't be too new.

I asked this question in another post, but I think this question could use its own thread.[/QUOTE]
If you don't want 3d acceleration, they pretty much all work.

---

### Post by Chucky G on 2006-05-14
The only problem I have with my current card is that I'm stuck at 640 x 480.  I can't change it.

---

### Post by xXx 0wn3d xXx on 2006-05-14
[QUOTE=Chucky G]The only problem I have with my current card is that I'm stuck at 640 x 480.  I can't change it.[/QUOTE]
Here is how to fix the screen res problem. In terminal type:


> sudo dpkg-reconfigure xserver-xorg

Then procede to answer the questions, it will basically pick the best things. When you get to the part that says "What resolutions would you like X to use ?" Uncheck the 3 at the bottom (using the space bar) and put a * in the box of the resolution that you want to use. Only select the one that you are going to use.

---

### Post by hw-tph on 2006-05-14
Matrox G400 or G450 should pretty much fit the bill I think. They are fully supported in Linux (no icky binary blob drivers but real Linux in-kernel and X.org drivers) and can be bought very cheap from Ebay. I think all G450 models are dual head.


Håkan

---

### Post by IYY on 2006-05-14
I'm pretty sure you don't need a new card. Look at MasterChief1234 solution, and also consider switching to the vesa driver (if that doesn't work).

---

