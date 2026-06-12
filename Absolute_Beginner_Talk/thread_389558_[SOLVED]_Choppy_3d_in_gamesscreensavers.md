---
title: "[SOLVED] Choppy 3d in games/screensavers"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-03-20
I have a Dell Dimension E510 with Ubuntu 6.10, Windows XP Media Center 2005, 3.4 Ghz Pentium 4 HT, 1GB Ram, ATI Radeon X600 256 MB Video Card, 120 GB HD. I am having trouble with my 3d rendering on games and screensavers. Basically, if I open any 3d game (i.e. neverputt) or try to change my screensaver to a 3d screensaver, the video is so choppy that it almost freezes. I KNOW my computer is capable of running these b/c I have run the windows version of neverputt in windows without a hitch. What is the problem? is there some way to fix this?

---

### Post by twikletoes on 2007-03-20
Make sure you are using the right driver for your graphics card. Then when you do that see if it works.

---

### Post by alienexplorers on 2007-03-20
Do you have the most current drivers for your video card installed.  What is you FPS.  Run "glxgears  -printfps".

---

### Post by ardchoille42 on 2007-03-20
Have you installed the drivers for your video card? If not, see [this how to]("https://help.ubuntu.com/community/BinaryDriverHowto").

I had the same problem with choppy videos and screensaver, but after installing the video drivers, the choppiness disappeared.

---

### Post by wcbardwell on 2007-03-20
I am trying to run 3d in Ubuntu 6.10. I'm a noob, so as simple as possible please.

---

### Post by wcbardwell on 2007-03-20
I just installed the ATI driver that was recommended and it didn't help... any ideas?

---

### Post by ardchoille42 on 2007-03-20
> **wcbardwell said:**
> I just installed the ATI driver that was recommended and it didn't help... any ideas?

Did you restart X? You need to restart X for the video drivers to load. You can restart X with:

```

sudo /etc/init.d/gdm restart

```

---

### Post by wcbardwell on 2007-03-20
I restarted it by holding Ctrl Alt Backspace. I've been using Ubuntu for a couple of weeks now and got a few of the tricks, but the 3d is still my last problem to fix.

---

### Post by wcbardwell on 2007-03-20
ok... i didn't look at the how to until just now. I ran through the setup for the "new" ATI driver... I've tried several times, but keep getting stuck. When I input:
```
fglrxinfo
```
I get
```
Xlib:   extension "XFree86-DRI" missing on display ":0.0".
display:  :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
Open GL version string: 1.2 (1.5 Mesa 6.5.1)
```

I tried the troubleshoooters

---

### Post by wcbardwell on 2007-03-20
still can't get it

---

### Post by wcbardwell on 2007-04-03
I got the driver to install finally, but now all of my 3D is black... no picture at all... just a black screen! help!

---

