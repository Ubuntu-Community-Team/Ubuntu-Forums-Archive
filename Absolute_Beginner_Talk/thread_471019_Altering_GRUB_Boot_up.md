---
title: "Altering GRUB Boot up"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2007-06-11
I appear to have loads of different Kernel versions that all appear on GRUB, how can I un-install these kernels and remove them from GRUB?

---

### Post by vasiliymeshko on 2007-06-11
You can search for, and remove them in Synaptic. It should update the GRUB menu accordingly

---

### Post by doobit on 2007-06-11
> **Captain Kirk76 said:**
> I appear to have loads of different Kernel versions that all appear on GRUB, how can I un-install these kernels and remove them from GRUB?

You could use Synaptic to uninstall them. Then just edit the file /boot/grub/menu.lst to get rid of the extra entries.

---

### Post by Captain Kirk76 on 2007-06-11
Where abouts in Synaptic is it?

---

### Post by bodhi.zazen on 2007-06-11
Use the search function.

Search for linux or kernel

Keep the current (highest numbered) and 1 old one (always good to have a known good kernel).

---

### Post by freesitebuilder on 2007-06-11
Will the oldest versions be removed from GRUB when new versions of Ubuntu are installed?

---

### Post by bodhi.zazen on 2007-06-11
> **freesitebuilder said:**
> Will the oldest versions be removed from GRUB when new versions of Ubuntu are installed?

No. You have to remove old kernels manually.

---

