---
title: "Can't complete Ubuntu installation"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by mistywindow on 2006-12-18
After 2 days of battling I can't complete the installation process for Ubuntu 6.10.

Everything procedes normally: boot from CD, install from live session, installation seems normal, reboot when prompted in GUI.

Then, when I reach the command line screen which says something like "remove disc and press Enter to continue"; the tray opens, I remove the disc, close the tray, press Enter and ***nothing ***happens.

The keyboard is still active because if I try Ctrl+Alt+Delete the screen refreshes, the CD tray reopens and the message reappears.

I have tried this with the both the 64 bit CD and DVD versions with the same result. I've used both USB and PS/2 keyboards. Discs have been error checked.

I've tried it on a dedicated 40GB IDE disc and on 40GB of free space on my second 250GB SATA disc.

If I reboot anyway, not surprisingly Grub won't load. ](*,) 

My system details:
AMD Athlon 64, 2000 MHz (10 x 200) 3200+
Motherboard Abit KN8 SLI
Chipset nVIDIA nForce4, AMD Hammer
Memory  2048 MB  (PC3200 DDR SDRAM)
BIOS Award (05/30/06)
Video Adapter NVIDIA GeForce 7600 GS  (512 MB)
Monitor Dell 2407WFP 
Drives:
2 x 250GB SATA
1 X 40GB IDE
1 x CD RW
1 X DVD RW

I've also tried the 32 bit CD version on another PC (Celeron 2GHz?) with the same result.

Help!

---

### Post by taurus on 2006-12-18
On the DVD, there is an alternate version so use that to install it on your machine then!!!  See if it will reboot after it finishes installing Ubuntu on your machine this time.

---

### Post by mistywindow on 2006-12-18
Thanks Taurus,
I installed using the text only method and that worked OK.
However, I now get a Grub Error 21 on booting.
This may be due to problems with the disk I've installed to. It's had an overlay on it and although Linux recognises it as 40GB, BIOS and Windows see it as 23GB. This may be creating confusion.
I'll try installing on one of my SATA drives and see what happens.
I'm most grateful for your help.

---

### Post by mistywindow on 2006-12-18
That did it Taurus!
Wish I'd asked 2 days ago :D

---

