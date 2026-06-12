---
title: "Remove Kernels from Bootloader"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by pbesing on 2007-07-09
My GRUB bootloader has multiple kernels from previous installations and upgrades.  How can I remove them so that I only have my current Ubuntu installation on the loader?

---

### Post by bigken on 2007-07-09
go into synaptic and remove them :)

---

### Post by UnixAnt on 2007-07-09
You could always get your hands dirty and edit the menu.lst file located in /boot/grub

Open this up and remove the extra entries, then save the file.

Synaptic is probably cleaner though...

---

### Post by pbesing on 2007-07-09
> **bigken said:**
> go into synaptic and remove them :)


Uh...duh..thanks..didn't realize it was that easy.

---

### Post by bigken on 2007-07-09
nothing is easy if you dont know this forum is great just ask and you will find your answer :)

---

### Post by lisati on 2007-07-09
> **bigken said:**
> nothing is easy if you dont know this forum is great just ask and you will find your answer :)
True!

---

### Post by Inxsible on 2007-07-09
Removing them from the menu.lst will not remove the kernel from the system, it will simply not list it in the menu options. Synaptic is the way to remove them. Search for the kernel number you want to remove.

Note: [COLOR=Red]Always keep atleast one older and stabler version around just in case your new kernel gives you problems.[/COLOR]

---

