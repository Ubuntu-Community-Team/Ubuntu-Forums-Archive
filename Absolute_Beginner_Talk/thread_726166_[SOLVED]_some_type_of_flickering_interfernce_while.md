---
title: "[SOLVED] some type of flickering interfernce while ingame"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2008-03-16
I am runninf 64 bit Ubuntu gutsy gibon on a freshly built Pc I installed the newest drivers for the video card and installed the 64 bit ps while I am ingame I get a flicker or a kind of pulse type of  interference I did a 
Code:

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870
OpenGL version string: 2.1.7412 Release

so I am sure the drivers are ok I also uninstalled the 64 bit and tryed the 32 bit ps and it was even worse. the pulsing looks allot like when you have a tape in a VCR and the tracking is off that is the best way for me to diskribe it. anyway I uninstlled the 32bit ps and reinstalled the 64bit because the interfence isn't as bad, I also have deul boot so I booted into windows and installed ps there and it has know problems at all so it has something to do with Linux and I really don't like windows and would prefer to play in Linux.
( confusing isn't it Smiley  ) can anyone help me with a fix?
I  read some where in one of the posts on here that someone had simular problems and changing to full screen corrected these problems so I tried that and received the following errors ( I hope this help narrows down the problem)
 Crystalspace.window.exrf86vm: unable to switch
Crystal space.canvas.glx2d:failed to open the x-windows
crystalspace,graphics3d.opengl:error opening graphics 2d context.
AT first I thought that it was the Planeshift game bit IO installed Enemy territory and it does exactly the same thing

---

### Post by forrestcupp on 2008-03-16
It's a known issue when using ATI proprietary drivers and running Compiz.  OpenGL stuff just flickers.  You have to turn Compiz off, either by turning off Visual Effects in Appearance, or by typing:
```
metacity --replace
```
Then you can turn Compiz back on after you're done with the game.

---

### Post by IsawSp4rks on 2008-03-16
Or you can use two nice gnome panel apps (either one or the other - no point in both at the same time) 

1. Fusion Icon : [http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/)

or

2. Compiz Switch : [http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/](http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/)

Both can disable/switch Compiz Fusion, but Fusion Icon also gives nicer management of Compiz Fusion and Emerald and allows you toggle between Metacity and Emerald as your window decorator.  I've used both (staring with Compiz Switch) but eventually settled on Fusion Icon as I found it be more versatile for my usage.

---

### Post by Shadowmeph on 2008-03-16
> **forrestcupp said:**
> It's a known issue when using ATI proprietary drivers and running Compiz.  OpenGL stuff just flickers.  You have to turn Compiz off, either by turning off Visual Effects in Appearance, or by typing:
```
metacity --replace
```
Then you can turn Compiz back on after you're done with the game.

wow that is totally cool thank you so much you made my day :)

---

### Post by locutus42 on 2008-04-01
FYI, still seeing the flickering of OpenGL apps with default install of Hardy beta and ATI restricted driver. Turning of Visual Effects( Normal is default ) stops OpenGL app flickering issues.

Compaq R4000, ATI Technologies Inc Radeon XPRESS 200M 128MB sideport and 128MB UMA
Linux version 2.6.24-12-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu4)) #1 SMP Wed Mar 12 23:01:54 UTC 2008

Generally quite impressed with Hardy so far.

---

