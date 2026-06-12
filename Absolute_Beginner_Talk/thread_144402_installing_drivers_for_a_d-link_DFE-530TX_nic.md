---
title: "installing drivers for a d-link DFE-530TX nic"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by unisol on 2006-03-14
i have been using breezy for a while i recently installed a d-link DFE-530TX nic in my system the driver is dlkfet-4.39.tar.gz i tried numerous times to install it to no avail can someone help please i think i found part of the problem when i try to run make install it wants gcc3.4 i have gcc 4.0 does anyone know if there are any newer drivers for my card

---

### Post by Pragmatist on 2006-03-14
Please post the **Makefile** here

---

### Post by promet on 2006-04-23
Unisol,

I believe you can make this work by forcing Ubuntu to compile with gcc version 3.4 (assuming it is installed on your system - probably is, Synaptic it if it isn't). Then, type this from the command line:

"export CC=gcc-3.4"

This will, temporarily (until next boot), set your CC environment variable to gcc version 3.4. Then try to rebuild the driver. Please let me know if this helps at all. Good luck (as I am about to try to install this driver myself! ;) ).

Cheers,
promet

---

