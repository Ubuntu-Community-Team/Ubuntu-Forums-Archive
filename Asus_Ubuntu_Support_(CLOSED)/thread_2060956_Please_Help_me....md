---
title: "Please Help me..."
date: 2012-09-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Bala Sasidhar on 2012-09-21
Hi.. I am using ASUS K53SC Notebook with 
i-5 Processor (2.4 GHz)
4 GB Ram
750 GB HDD
1 GB NVIDIA Geforce GT 520MX  Graphic card.
I was sucessfully installed NVIDIA Driver "NVIDIA-Linux-X36-304.43" (Downloded from Nvidia site).

When I try to open NVIDIA X serve settings it Displays an error as "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

After running the Command "nvidia-xconfig" my screen resolution is restricted to 640x480.

How can I over Come this problem and use the NVIDIA Controll panel. ?

please help me...

---

### Post by jerrrys on 2012-09-21
I do not run the 304 driver, but know of this

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=304+drivers&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=304+drivers&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Geezanansa on 2012-10-23
try "lsmod" or "lspci -v"  in  cli/terminal to confirm what driver you are using and what modules are loaded in desktop session.
Did you stop nouveau from loading and blackist and change xserver runlevel before attempting to install nvidia 304??

See Nvidia readme [http://uk.download.nvidia.com/XFree86/Linux-x86/304.60/README/commonproblems.html#nouveau](http://uk.download.nvidia.com/XFree86/Linux-x86/304.60/README/commonproblems.html#nouveau)

Nvidia readme 

sudo nvidia-xconfig from cli should get you going if your driver is correctly installed

---

