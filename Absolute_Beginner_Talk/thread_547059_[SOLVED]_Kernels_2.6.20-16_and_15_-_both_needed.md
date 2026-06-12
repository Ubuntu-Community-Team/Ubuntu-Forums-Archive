---
title: "[SOLVED] Kernels 2.6.20-16 and 15 - both needed?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-09-09
Both of these kernels show on my boot menu. Do I need both? Can I remove the older one, as anything that will free up space on my machine would be welcome?

And how would I go about doing so? I can't see anything in Synaptic

---

### Post by cotcot on 2007-09-09
You can delete the oldest one after you have checked that booting in the new one works fine.

---

### Post by por100pre1 on 2007-09-09
If disk space is not a problem, keep two kernels at least. Some kernel updates can be troublesome and an old spare kernel can be a lifesaver in those situations.

---

### Post by mikeyphi on 2007-09-09
> **qprfact said:**
> Both of these kernels show on my boot menu. Do I need both? Can I remove the older one, as anything that will free up space on my machine would be welcome?

And how would I go about doing so? I can't see anything in Synaptic

Leave the two kernels - but you could clean out the old packages:
Open a terminal and enter:
sudo apt-get clean

---

### Post by qprfact on 2007-09-09
OK! But just so I know, how DO I delete a kernel?

---

### Post by sailor2001 on 2007-09-09
in synaptics: linux-image for the kernel you want to remove

---

