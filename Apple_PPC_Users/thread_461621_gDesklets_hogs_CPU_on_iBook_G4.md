---
title: "gDesklets hogs CPU on iBook G4"
date: 2007-06-01
forum: Apple PPC Users
---

### Post by reh4c on 2007-06-01
Overall, Feisty runs great on my iBook G4.  I did have to reset the PMU after the laptop suddenly shutdown and wouldn't turn back on.  After reseting it and adjusting the date & time, it seems to be working fine.  However, during this fiasco, I noticed that my CPU was running at nearly 100% continuously.  After checking the system log, I found gDesklets was hogging the CPU (not RAM), which caused terrible battery life and other system "stress".  After disabling gDesklets, the system is running very smooth, and the CPU scales accordingly.  Is gDesklets known to hog the CPU?  Is there a way to fix it?  I do miss my desktop calendar and clock ;)  Thanks.

---

### Post by stmiller on 2007-06-01
Hey I'll install gDesklets on my G4 TiBook and mess around to investigate. gDesklets is supposed to be very good on resources. It could be a poorly written gadget/widget (whatever they are called).

---

### Post by reh4c on 2007-06-02
> **stmiller said:**
> Hey I'll install gDesklets on my G4 TiBook and mess around to investigate. gDesklets is supposed to be very good on resources. It could be a poorly written gadget/widget (whatever they are called).

The e-mail checker "thingy" appears to be the memory hog.  I deleted it from my desktop, and CPU usage fell to well below 20% idling...even with desktop effects enabled.  I was suspicious of the mail checker from the start!  Is there a way to get it fixed?  Contact the developer?

---

