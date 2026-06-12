---
title: "ATI RADEON XPRESS 200M + Google Earth + Feisty Fawn"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by vmsda on 2007-10-07
The above combination is giving me a slight headache. Today I got Google Earth from the Medibuntu repositories, but whether I launch it from Applications > Internet or from a Terminal window, the result is the same:

     1. A Google Earth window opens but stays "initializing" forever;
     2. I get the following message on the terminal window:

         "Xlib:  extension "XFree86-DRI" missing on display ":0.0".

An _[COLOR="Black"]lspci[/COLOR]_ command gives the following result:
     "...
      01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 
      5955 (PCIE)
      ..."

An _[COLOR="Black"]fglrxinfo[/COLOR]_ command gives the following result:
     "Xlib:  extension "XFree86-DRI" missing on display ":0.0".
      display: :0.0  screen: 0
      OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
      OpenGL renderer string: Mesa GLX Indirect
      OpenGL version string: 1.4 (1.5 Mesa 6.5.2)"

Can anybody give this ignoramus a few heavy hints on how to solve the problem?

---

### Post by Sklasko on 2007-10-07
Follow the directions of [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") to get 3D hardware acceleration on your ATI working properly.

I've got the exact same ATI model in my Compaq Presario V2000 and these drivers have worked since Dapper.

Edit: Oh, forgot to mention, use Method 2 in the guide. You'll want the newest drivers.

---

### Post by vmsda on 2007-10-08
> **Sklasko said:**
> Follow the directions of [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") to get 3D hardware acceleration on your ATI working properly ...
Edit: Oh, forgot to mention, use Method 2 in the guide. You'll want the newest drivers.

Thank you, Sklasko. I followed the instructions religiously, but it does not work (yet!): when I start up, the screen displays 4 pairs of vertical white lines, they flash briefly and then I get a black screen until I power off. However, when I now submit the command _fglrxinfo_ this is the reply:
     "fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared 
      object file: No such file or directory"

I resolved the missing library problem by setting libGL.so.1 as a symbolic link to libGL.so.1.2. Additionally (and contrary to what the instructions doc says), the "volatile" dir already existed, so deleted its contents so I could symlink it as per instructions in the doc.Then I configured the driver again as per instructions in order to get the proper xorg.conf, and restarted. Unfortunately, the result is the same. So I did some digging in /var/log/Xorg.0.old and this is what I found (among other stuff):

.......
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON XPRESS 200M Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
......
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x40000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc8000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
....

I hope this throws some light. Grateful for your help.

---

