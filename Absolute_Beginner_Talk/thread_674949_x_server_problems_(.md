---
title: "x server problems ("
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by bruno9779 on 2008-01-22
I have recently tried to install "Kohan immortal sovreigns", but it messed up my Xserver conf: I couldn't change the definition of my laptop (compaq v6000 spanish layout) in any way.
Searching trough the forums I have found a command line to reconfigure X:

 sudo dpkg-reconfigure xserver-xorg

it worked fine for the monitor, but I messed up the keyboard.
I can't make sense of the options given by X reconfigure, so I have tried  the graphic way:

toolbar system > preferences > keyboard 

and I get the following error message:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

I have reinstalled all the libraries involved and somehow restored my keyboard settings, but the graphical interface keeps giving me the error message above (4 or 5 at the time)

Thankx!

---

### Post by sirgogo on 2008-01-23
Hello Bruno,

First off I just wanted to say, try running this instead. Its basically the same thing, but it's worth a shot:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```.
That usually auto-configures it when you are having errors. I understand you used a similar code, but sometimes the difference can just be a tag.

So, concerning your issue:
-What graphics/video card are you using?
-Are you connected to the internet?
-Did the settings work on your first install?

Let me know, so we can figure out a solution.

---

