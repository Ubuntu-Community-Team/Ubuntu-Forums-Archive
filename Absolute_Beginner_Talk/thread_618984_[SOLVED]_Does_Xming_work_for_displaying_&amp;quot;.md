---
title: "[SOLVED] Does Xming work for displaying &amp;quot;full desktop environment&amp;quot; ?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-11-21
I've installed SSH on my Xubuntu Box, and installed Xming and Xming Fonts on my WinXP box, I am able to launch apps via putty for example... ```
xeyes
gedit test.tmp
```
Launches xeyes and gedit in WinXP respectively, but what I really want to do is open up my whole desktop remotely using Xming, is this possible, what is the command I need to put in SSH/Putty to get this to work?
I am looking to use Xming as a VNC replacement sorta, since I [can't seem to get TightVNC to work properly :(](http://ubuntuforums.org/showthread.php?t=618937), is it possible to use Xming to get the "full desktop environment", or am I barking up the wrong tree?
TIA,
-BassKozz

---

### Post by BassKozz on 2007-11-21
I've installed SSH on my Xubuntu Box, and installed Xming and Xming Fonts on my WinXP box, I am able to launch apps via putty for example... ```
xeyes
gedit test.tmp
```
Launches xeyes and gedit in WinXP respectively, but what I really want to do is open up my whole desktop remotely using Xming, is this possible, what is the command I need to put in SSH/Putty to get this to work?
I am looking to use Xming as a VNC replacement sorta, since I [can't seem to get TightVNC to work properly :(](http://ubuntuforums.org/showthread.php?t=618937), is it possible to use Xming to get the "full desktop environment", or am I barking up the wrong tree?
TIA,
-BassKozz

---

### Post by BassKozz on 2007-11-21
Question Moved: [http://ubuntuforums.org/showthread.php?p=3814176](http://ubuntuforums.org/showthread.php?p=3814176)

---

### Post by BassKozz on 2007-12-13
Figured it out thanks to this post: [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

All I had to do was replace the code in **~/.vnc/xstartup** with ```
##!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid navy # Choose your color
x-window-manager &
{
 (gnome-panel 2> /dev/null &)
}
xterm &
```And now I simply run "**~/.vnc/xstartup**" from Putty, and up comes the desktop :)

---

