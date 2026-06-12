---
title: "Distorted Windows"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by LinuxIsInnovation on 2007-12-20
I am facing a peculiar problem here.
When any of my application window opens (like Firefox, Evolution, Openoffice.org, etc) the open-up animation is not shown. Rather, the window appears in a peculiar way.
Here is a screenshot I took immediately when the Evolution window was opening:

[ATTACH]53778[/ATTACH]

This looks pathectic. I have tried disabling certain plugins and tried again, but in vain. I removed some apps, reinstalled them, but nothing happened.

Please tell me what to do.

Heres what happens when i start compiz from the terminal:
glade@Muzic-Jukebox:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


I have Intel GMA950.

---

### Post by LinuxIsInnovation on 2007-12-20
Also, mine is a 64-bit edition of Gusty.

---

### Post by LinuxIsInnovation on 2007-12-21
Bump.

---

### Post by LinuxIsInnovation on 2007-12-21
Can no1 solve this? Isn't anyone else facing this problem?

---

### Post by mikeym on 2008-01-09
I am! It only appears to occur when I'm using WM programs with compositing so I presume it has something to do with that. 

So far Compiz and XFCE with compositor enabled have the same problem. 

This is a screen shot of XFWM4 with compositing enabled experiencing the same problem. 
[[IMG]http://img262.imageshack.us/img262/548/screenshotlt8.th.png[/IMG]](http://img262.imageshack.us/my.php?image=screenshotlt8.png)

I have NVIDIA GForce 8600 GTS with 100.14.19 drivers installed.

Does anyone know that the issue is?

---

### Post by mikeym on 2008-01-09
I'm also incidentally using 64bit gusty

---

### Post by mikeym on 2008-01-11
I'm trying to pursue this on the nvnews forum that the NVIDIA support people help out on but so far I've been stonewalled.

[http://www.nvnews.net/vbulletin/showthread.php?t=105919](http://www.nvnews.net/vbulletin/showthread.php?t=105919)

---

### Post by marufaberlin on 2008-01-11
You might want to install the package compiz-config-settings-manager, and uncheck the checkbox next to "wobbly windows" in the advanced appearance settings.

---

### Post by mikeym on 2008-01-11
Ummm.. I'm not even running compiz. This is a general problem with the proprietary drivers from NVIDIA with (it seems any) compositing on Ubuntu. 

This thread is about compiz; I've had the same issue on compiz and have the exact same problem on XFCE when compositing is enabled and I have had reports that the same problem is found on KDE compositor.

---

