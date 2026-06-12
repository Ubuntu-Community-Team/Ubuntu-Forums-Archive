---
title: "less intence effects windows manager then compiz..?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-01-14
If I just want fading windows and drop shaddow, is there a less intensive windows manager? I've heard of this drop shaddow thing for X manager.. could not get it working though...

i know you can turn off settings with ccsm in compiz, but i'm curious if there is any alternatives...

like more pretty then "window maker" but less then "compiz" and a little more effect then "metacity"

sv

---

### Post by jordanmthomas on 2008-01-14
xcompmgr?  It's not a window managaer but will give you fading, transparency, and shadows
e16 or e17 (enlightenment) may be up your alley as well.

edit
Also, you can turn the effects in compiz way down and have essentially metacity.  Then, add effects until they're too much for you.

---

### Post by staticvoid on 2008-01-14
cool thanx, i'll give xcompmgr another shot,

and with a lower compiz effects will it take up less CPU?

sv

---

### Post by jordanmthomas on 2008-01-14
Well, for me, compiz doesn't eat too much time anyway but I have pretty modest settings.

But yes, the less it's having to do, the less cpu / gpu time it will take up.

For me, compiz with just shadows / fading is much faster than xcompmgr with fading and shadows.  I use xcompmgr with window managers like awesome, dwm, wmii, etc and it works very well if you just use it to draw shadows:
```
xcompmgr -cC
```

---

### Post by staticvoid on 2008-01-14
yeah thats the best solution for me...
[http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527)

> sudo apt-get install transset xcompmgr
sudo gedit /etc/X11/xorg.conf

add:

Section "Extensions"
   Option  "Composite"     "Enable"
EndSection

do Ctrl + Alt + Backspace to restart X

then run:

xcompmgr -cC -t-3 -l-5 -r5
and try for fun:
transset .5 (then click on a window)

my little howto :) for more xcompmgr settings check the link. add this to your sessions (System>Preferences>Sessions)

command:
xcompmgr -cC -t-3 -l-5 -r5 & killall gnome-panel

fun stuff!!!  :D

---

### Post by staticvoid on 2008-01-14
huh... how can I avoid this:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-18.png[/IMG]

hmm.. annoying fat gray thing when moving icons...

sv

---

### Post by jordanmthomas on 2008-01-14
Use compiz instead?
:)

Honestly, though, I don't believe xcompmgr has the ability to filter out certain window types like compiz does.

---

### Post by staticvoid on 2008-01-15
well... like I said, all I want is drop shaddows (and fading windows, but I changed my mind)... how would I go about programming that? xml? python? 

I'd use compiz.. but why can't I just have a drop shaddow for my windows without a bunch of bugs?

hmm...

sv

---

