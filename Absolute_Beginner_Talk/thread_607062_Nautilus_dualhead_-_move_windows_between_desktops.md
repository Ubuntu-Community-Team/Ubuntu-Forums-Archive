---
title: "Nautilus dualhead - move windows between desktops"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by cronfy on 2007-11-08
Hello!

I am using Ubuntu 7.10 with Gnome.

I have just set up dualhead with ATI proprietary drivers (aticonfig --initial=dual-head). Everything works just fine, I have one desktop on the right of another. I can move mouse and desktop icons between desktops and it is possible to run applications on each. But I cannot move windows between desktops -- moved window part does not appear on another  desktop, it is just cut. That means that if I want to use application on specific desktop, I must initially run it there. Moving window to right/left workspace does not move windows between desktops.

How can I move window to another desktop?

Thanks.

---

### Post by skanchi on 2007-11-11
You need to enable xinerama option in the X configuration. please refer X configuration help on this

---

### Post by WinterWeaver on 2007-11-11
It's also possible, since you have Gutsy, that you might have compiz and wall/cube enabled... the edge of your window is probably moving onto the "virtual" desktop.

---

### Post by WinterWeaver on 2007-11-11
You can test this theory by doing the following:

Drag your window to the edge, until it gets cut of.
let it sit there, and now press: ctrl-alt-right (assuming you dragged it to the right edge)

If your desktop pans on that view, and you see the window edge on this other desktop, then this is the case...
let us know your findings :)

---

### Post by cronfy on 2007-11-14
Thanks for the answers! 

**skanchi**, as far as I understand Release Notes for 7.10, Xinerama support was dropped for ati drivers:

> Dual-head (multi-screen) setups:

      The ati driver has dropped MergedFB / Xinerama support in favour of xrandr 1.2 support, and old multi-head xorg.conf setups will break. To set up dual-head see the guides at [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) or [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

I cannot use open source 'ati' or 'radeon' drivers, they do not work for my Radeon X2300. Thus I am using fglrx, but I do not completely understand how I can mix 'fglrx' with Xinerama and how Gutsy supports it.

**WinterWeaver**, I tried to switch to another workspace with bottom right switch, but it did not help - I can not see my window there. I'll try to use ctrl-alt-right though, but I do not think it will help.

I am not using Compiz, because I cannot enable desktop effects at all ;-)

---

### Post by cronfy on 2007-11-20
Ok, I have tested the theory with ctrl-alt-right. It does not work - I can not see part of a window that placed behind desktop border.

So, the question is still open:

I have dualhead config for ATI videocard with fglrx driver. I use Gnome with Nauitlus. This config gives me TWO UNDEPENDENT desktops, with 2 workspaces on each. I may move icons (i.e. CD-ROM shortcut) between desktops (that means between monitors). But I cannot move window between desktops - I must initially run application on that desktop I want to work with the application.

**Question is: how can I move windows between desktops?**

Thanks in advance.

---

### Post by beruic on 2008-05-13
I have the same problem. I would like to be able to drag a window from one desktop to another, like it is possible on eg. Fluxbox.

However it is possible moving a windows from one desktop to another by right-clicking the window title, or it's button on in the window list, and choose to move it to another workspace.

---

