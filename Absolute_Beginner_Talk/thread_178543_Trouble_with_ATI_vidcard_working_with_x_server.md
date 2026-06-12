---
title: "Trouble with ATI vidcard working with x server"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by Israfel on 2006-05-17
I recently downloaded kubuntu and installed it in a sepparate partition from my winXP for dual booting.I'm using a Toshiba Satellite L25-S1215 with an ATI Radeon XPRESS 200M series vidcard. When I start kubuntu, i have to hit ctrl+alt+f1 to get to a screen where I can log in (command line log in). I tried startx to load the GUI but it didn't work. I adjusted things with sudo dpkg-reconfigure xserver-xorg, but to no avail.  The errors i get when I use startx without changing anything with sudo dpkg-reconfigure xserver-xorg are;
Unable to find a valid frame buffer device, RADEON (0): Failed to open frame buffer device, RADEON (0): [dri] DRIScreeInit failed. Disabling DRI, Fatal server error: Caught signal 4. Server aborting, and XIO: fatal IO error 104 (Connection reset by peer) on xserver ":0.0" after 0 requests (0 known processed) with 0 events remaining. I have been fruitlessly trying several things and have been completely thwarted by the problem. Does anyone know what to do about this?

---

### Post by Israfel on 2006-05-18
I've heard of similar problems with the x server, but does anyone know how to remedy this? Should I try another version of Kubuntu?

---

### Post by richbarna on 2006-05-18
If you don't mind doing a reinstall, I would recommebnd choosing the "server" install only. Then when it's all done, after you get the usual login prompt and have entered your Login and Password, download the KDE Desktop.
I can't guaruntee that it'll work for you, but it did work on my Toshiba Satellite.
Download KDE Desktop :-
> sudo apt-get install kde

---

### Post by Mustard on 2006-05-18
Have you tried running the gui with 'vesa' drivers instead?

---

### Post by richbarna on 2006-05-19
[QUOTE=Mustard]Have you tried running the gui with 'vesa' drivers instead?[/QUOTE]
Mustard has a point, once I got the system up, I had an offset screen, so I changed to vesa drivers :-

> sudo kate etc/X11/xorg.conf

Then look for the drivers, and where it says "ati", change it to vesa.

---

### Post by adam.tropics on 2006-05-19
If you're using 5.10, then, at least for me, the supplied ATI driver doesn't work (Satellite with Radeon Xpress 200m). Use the vesa driver to get up and running, after the initial update the **newer** 'ati' will work, and then you should look at getting fglrx up and running either from ati.com, or wait till you upgrade to Dapper, it's in the restricted modules now.

---

### Post by Israfel on 2006-05-19
I've tried to vesa but couldn't get it to work either. (sorry bouy the slow response, had to be away for a bit).

---

