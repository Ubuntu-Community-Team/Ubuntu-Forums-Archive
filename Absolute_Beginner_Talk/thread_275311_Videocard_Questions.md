---
title: "Videocard Questions"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by StormGuy on 2006-10-11
I've tried booting up using the Live CD, but my videocard is giving me trouble :( .  It says it's an Nvidia if I look at the device manager in Windows...but when I open it up, it's an Asus.  It's a Geforce 6600. 

Is there anything I can do to configure my card so that it's compatible with Ubuntu.  I'd hate to have to regress to an inferior card.

---

### Post by tucoz on 2006-10-11
> **StormGuy said:**
> It says it's an Nvidia if I look at the device manager in Windows...but when I open it up, it's an Asus.  It's a Geforce 6600.

The Geforce 6600 _is_ a Nvidia chipset. But the manufacturer of the board itself is Asus in your case. So, you should use an nvidia driver in ubuntu. If that fails, try vesa.

---

### Post by StormGuy on 2006-10-11
Alright, so it's just a driver issue?  That's good to hear.  I can install using a different card and then get the drivers for my Nvidia.  Thanks

---

### Post by tucoz on 2006-10-11
or you can select the vesa driver. That will most certainly work, but will not give you all the features of your card.

---

