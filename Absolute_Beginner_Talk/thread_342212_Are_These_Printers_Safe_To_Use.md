---
title: "Are These Printers Safe To Use?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by corypina on 2007-01-19
I'm going to be purchasing a printer, and I've been looking at the printer compatibility data on linuxprinting.org. I'm wondering if I have to match the driver exactly to the printer I buy.

As an example:
If I go buy an HP PS C4180, can I use the driver for PhotoSmart C4100?  The driver is said to work perfectly, but will it work perfectly with this slightly different model?

---

### Post by MetalMusicAddict on 2007-01-19
I would *think* its a safe bet. I have a HP PhotoSmart 8450 that uses the 8400 driver. No issues here.

---

### Post by corypina on 2007-01-19
Thanks. Anyone else having success with something like that?

---

### Post by Sef on 2007-01-19
> If I go buy an HP PS C4180, can I use the driver for PhotoSmart C4100? The driver is said to work perfectly, but will it work perfectly with this slightly different model?

Ubuntu should have the PhotoSmart 4180 driver.   System > Administration > Printing.  Just click foward and not install when you get to that point.

---

### Post by meng on 2007-01-19
PSC2510 uses the PSC2500 driver. Mind you, the PSC2500 driver is just hpijs, which covers a LOT of models.

---

### Post by corypina on 2007-01-20
The 4180 doesn't show up in my list.
I've done all my updates, but noticed that the version of hpijs that shows up under "driver" is HPLIP 0.9.7.

I've attempted to install 1.6.12 as it's the current version.  Everything seemed to work fine, but 0.9.7 still shows up, even after following all directions from the HPLIP Sourceforge page.

Any ideas?

Thanks for all your help.

---

### Post by 11hjpphty76lkjj on 2007-01-24
What do you mean hplip 0.9.7 still 'shows up'? Can you run hp-check and post that?

---

