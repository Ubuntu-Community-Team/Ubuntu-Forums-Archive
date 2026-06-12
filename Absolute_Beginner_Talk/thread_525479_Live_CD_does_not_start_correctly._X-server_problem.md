---
title: "Live CD does not start correctly. X-server problem."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by El_Belgicano on 2007-08-14
While starting the live cd, an error come up telling me that the X-server could not be configured correctly and my live CD does not complete the opening of Ubuntu from the CD ...
Could Vista be the cause of my problems or is the laptop's architecture not the right for Feisty Live CD ????
** Asus Laptop with 120GB, 512 RAM Intel 2 Core Duo.
Thnx

---

### Post by nvrpunk on 2007-08-14
try the alternative cd.

---

### Post by S15_88 on 2007-08-14
wats ur graphics card?

---

### Post by El_Belgicano on 2007-08-14
Graphics: ATI Mobility Radeon X2300 External 128 Mo VRAM
nvrpunk: I don't believe thats the problem, cause I already used that same CD to install Ubuntu on another laptop.

---

### Post by Alterax on 2007-08-14
Not a Vista problem.  The only place where the twain would meet is at the bootloader, AFTER Ubuntu is installed, and that's only in selecting which one to hand over to the PC.

The problem is that your card is not working with the X11 server.  Your best bet is when it fails to type "sudo nano /etc/X11/xorg.conf" once X11 fails (I am assuming it goes to a shell, but if not, CTRL-ALT-F1)

Find the part where it gives the driver and change the driver to VESA.  That's pretty much a fail-safe.  Hit CTRL-X then Y.  Then type startx and you should be good to go.  

That will get you into the installer, once it is installed you may have to do the same trick to get it running until you add the proprietary drivers (restricted) repository and have it install the ATI fglrx drivers.

After that, all should be good.

---

