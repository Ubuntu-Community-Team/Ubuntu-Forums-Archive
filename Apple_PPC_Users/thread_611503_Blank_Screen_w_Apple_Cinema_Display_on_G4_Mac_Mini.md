---
title: "Blank Screen w Apple Cinema Display on G4 Mac Mini (Gutsy 7.10)"
date: 2007-11-13
forum: Apple PPC Users
---

### Post by Nelli on 2007-11-13
I am a very frustrated linux newbie.  I can't get the darn apple cinema display to work. I had this problem when I used a micron monitor and putting the option"MacModel" "mini" fixed it (tried it with and without).  Trying to use my new display no mater what I try,  I just get a blank screen.  I've been messin with xorg.conf, changing
resolutions settings , H/V refresh rates, and the driver (ati, vga, won't give me vesa). I also tried redetecting the graphics using dpkg-reconfig xserver (tried ati, and vga, again won't give me vesa (unless vesa is vga)). so far, when using the xinit -- :2 command, if it doesn't work I get back to the terminal with the err mgs
Radeon(0) No Valid modes.
Screen(s) found but no usable configuration.
 If something seems to work I just get a blank (black) screen. when I loaded 6.10 for comparison,  I got the same with the ati driver, and lines with vesa driver but it worked when I changed the res to 1024x786.  I don't know what else to do.:confused:

---

