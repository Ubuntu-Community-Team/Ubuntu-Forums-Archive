---
title: "Asus UL50VT Ubuntu10.04 Nvidia Card Boot Error"
date: 2011-07-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Loophead on 2011-07-18
Hi there,

I'm really stuck with my Asus UL50VT, dual boot(Ubuntu 10.04 Lucid Lynx/Windows 7).
I've been having problems with hybrid graphic card Nvidia GEFORCE G210M for some time, getting a blank screen at ubuntu startup.

I followed these steps to solve that issue:
1-At boot, press 'e' to edit the GRUB menu.
2-Using the arrow keys to navigate, delete "quiet" and "splash" 
3-Replace it by "nomodeset"
4-Press Ctrl and X to boot.

After that, GRUB started but got blocked at this line
"EXT3-fs error (device sda1): ext3_lookup: deleted inode referenced: 309473"

Can anyone help?

---

