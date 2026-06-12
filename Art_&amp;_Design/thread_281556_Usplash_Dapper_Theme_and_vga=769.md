---
title: "Usplash Dapper Theme and vga=769"
date: 2006-10-21
forum: Art &amp; Design
---

### Post by nothere on 2006-10-21
Hi
I do own a laptop based on nvida graphics chip.
In order to be able to switch between X screen and virtual terminals with <ctrl> <alt> <FN> keys properly i had to set the vga kernelparameter to "vga=769". This switches the framebuffer in 640x480 mode with 256 colors. Any other mode either with higher resolution or more colorbits 16/24 results in flickering and distorted display of the virtual terminals.

The workaround by setting vga=769 is ok for me but causes the kubuntu usplash theme be displayed in a bit strange colors (some parts of the logo appear in red and other colors but not blue). The same holds for the progress bar and Text. Both are mapped to slightly strange cloros (Nothig eye braking).

Thus i'm asking wold it be possible that the usplash themes are also tested against framebuffer mode 640x480x256 and not only against the highcolor and true color modes? Or do you allready know some fix for the 8 bit color frame buffer modes? Or is it that only nvidia chips do not properly initialize palette in 256 color mode?

Yours
Xris

---

