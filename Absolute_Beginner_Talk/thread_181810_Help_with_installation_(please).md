---
title: "Help with installation (please)"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by justlisawv on 2006-05-24
I have put Ubuntu on an older computer. I added memory to it and a larger hard disk, but after everything has installed, I am seeing three faint desktops and cursors on the screen.  I can put in my name and password and barely see that it moves on from there.  I am using an older (maybe VGA) monitor and the video card that was on the motherboard, I am thinking it is a video problem, maybe resolution setting, not sure how to change it however without going into the program. Any help would be appreciated.

---

### Post by popkid on 2006-05-24
[QUOTE=justlisawv]I have put Ubuntu on an older computer. I added memory to it and a larger hard disk, but after everything has installed, I am seeing three faint desktops and cursors on the screen.  I can put in my name and password and barely see that it moves on from there.  I am using an older (maybe VGA) monitor and the video card that was on the motherboard, I am thinking it is a video problem, maybe resolution setting, not sure how to change it however without going into the program. Any help would be appreciated.[/QUOTE]

When you say "desktops" I'm guessing you are at a graphical log in...

Could be just x not configured correctly (the graphical display system in linux)

try pressing alt+ctrl+F2

This should bring up a text login shell... does this display correctly?

If it does, then login at that text prompt and type in

sudo dpkg-reconfigure xserver-xorg

then follow the instructions,

you should find that if that works ok, X should work when you reboot (ctrl-alt-del should reboot you from text shell)

pK

---

### Post by justlisawv on 2006-05-24
Thanks, it was actually the lack of a SVGA monitor.  I am using it now (first time with a Linux system) and loving the looks of it! :KS

---

