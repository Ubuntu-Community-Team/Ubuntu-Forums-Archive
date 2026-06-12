---
title: "usb keyboard and booting"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-04-11
I have a usb keyboard on this computer and it appears that it is not recognized until sometime after the system boots. This prevents me from tabbing down to safe mode in the grub bootloader. I haven't needed to do it (yet ;-)), but would like to know what, if anything I can do. If I plug in a normal ps2 keyboard, it works OK. The keyboard is a Microsoft 4000.

That fixed it, thanks. The funny thing is that it recognized the F2 to get into the bios, but not after that until it launched. 

For info, I turned on USB emulation in the bios.

---

### Post by chewearn on 2007-04-11
Look into your BIOS setup, see if there is a setting to enable/disable USB keyboard support.

---

