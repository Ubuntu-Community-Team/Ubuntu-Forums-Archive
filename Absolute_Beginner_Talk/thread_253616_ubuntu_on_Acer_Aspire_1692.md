---
title: "ubuntu on Acer Aspire 1692"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Chris Val Kef on 2006-09-08
hey there! i'm totally new to linux - ubuntu community so be gentle!

i decided to install ubuntu (6.06.1 desktop i386) on my Acer Aspire 1692 laptop. I boot from the cd and selected 'install or start ubuntu...' to try them first. 
After some minutes of proccessing (mount, install drivers or something...) i heard a sound looked like logging in (sorry for the  comparison, but like when windows are starting) and then only darkness! 
nothing but a black widescreen and nothing that i can do!
even the start button to restart laptop didn't respond. so i got to take of the battery and place it again in order to eject the cd just before boot.

Any ideas? thought it's the video card but i'm not sure. I didn't try the safe video mode...

Intel Pentium M processor 740 (1.73GHz, 533 MHz FSB, 2MB L2 cache)
Ati Mobility Radeon X700 PCI Express 256 VRAM
Toshiba 80GB HDD
Slot-loading DVD-dual Lite-On 8x
1GB DDR2 (supporting dual-channel)
wifi, bluetooth etc...

---

### Post by Kobalt on 2006-09-08
Hello,

This is a common problem : to solve it, select at the very first menu you get when booting on the CD (start Ubuntu, etc...) the last option "start with custom command" (or something like that, I can't remember properly). Then type : 
```
install vga=771
```

Now you should get proper graphical settings and be able to log in.

Welcome into Ubuntu,

Cheerios !

---

### Post by Chris Val Kef on 2006-09-08
thanx! I'll try it later and let you know!

---

### Post by daikrieg on 2006-10-25
The best way is using the alternate install CD, adding the install option "noapic" (without the ""). After installing, the X crashes, allright. Press Ctrl+Alt+F1 to go to a prompt. Log and type: 

$ sudo nano /etc/X11/xorg.conf 

Find the block "Device" and, at the end (below "option") type: 

Option Monitorlayout "LVDS" 

Ctrl+O to save, Ctrl+X to exit, and then restart the grafic session 

$ sudo /etc/init.d/gdm restart

It should work, i got the same book. If it doesn´t, replace the LVDS with TMDS.


Good bye and good luck!

---

### Post by chatuser on 2006-10-26
I have proceeded this way using Edgy Eft 6.10:

1. Custom commands
... vga=711 noapic acpi=off

2. $ sudo nano /etc/X11/xorg.conf
Find the block "Device" and, at the end (below "option") type:
Option Monitorlayout "LVDS" --> with 5.10 I used "LVDS,TMDS" but now 6 little screens are displayed
Ctrl+O to save, Ctrl+X to exit, and then restart the grafic session

3. $ sudo /etc/init.d/gdm restart
It retrieves "failed" starting gdm. After some killall's gdm starts ok but instead the desktop a white window is displayed

How can I start the desktop properly to install 6.10 ?

---

### Post by chatuser on 2006-10-27
I answer myself ;) 

1. Use alternate CD and press F6-Additional Parameters
2. Add vga=771 to the default parameters. It is no longer necessary specify noapic
3. DO NOT specify acpi=off, your network cards will not work !
4. The system boots rigth but the splash screen is shifted to rigth
5. When the blank screen appears, press Ctrl+Alt+F1
6. sudo nano /etc/X11/xorg.conf

7. Search Section "Device" and add:
Option "MonitorLayout" "LVDS"
DO NOT specify "LVDS, TMDS" or several little screens will appear

7. ^O, ^X

---

### Post by coolix on 2006-11-01
This is how I proceed with the ubuntu 6.10 desktop 386 Live CD:

1. On boot menu press F6, remove 'splash' and add 'vga=771'
2. `sudo vi /etc/X11/xorg.conf` and replace 'ati' with 'vesa'
3. `sudo /etc/init.d/gdm stop`
4. `startx`

From here, you'll get your screen back and be ready to install !

---

