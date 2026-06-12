---
title: "&quot;sudo dpkg-reconfigure xserver-xorg&quot; probs"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by gord on 2005-08-11
hey;

im having some problems with using the program that runs behind:
```
sudo dpkg-reconfigure xserver-xorg
```

its not any permitions problems or anything like that. its just the last time i ran it (just after installing ubuntu) i did everything on it but then goto some stuff that i didn't understand so well (it had apprently autodetected my graphics card so i just trusted it), and then when i rebooted i couldn't get to the desktop at all and was stuck in a CLI.

anyone have any suggestions? if its one of those things where you really have to know what your doing, then im sure that i can live with 1024x768... i just don't want to mess it up again and have to re-install ubuntu again, iv got it configured pritty well and it would take hours to get it back to this condition.

any help is deaply appreciated :)

---

### Post by xmastree on 2005-08-11
[QUOTE=gord]iv got it configured pritty well and it would take hours to get it back to this condition.[/QUOTE]Well, before you go messing with it again,[COLOR=Red] **backup your config file**[/COLOR] [-X ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back
``` Then, next time you break your x server, and you're back at the cli, do:```
sudo cp /etc/X11/xorg.back /etc/X11/xorg.conf
```And you're back at 'this condition' in seconds, not hours.

Backed it up? Now, go ahead and play.  :)

---

### Post by gord on 2005-08-11
ahh thanks very much :) 

i wish all support forums were as great as this -_-

---

### Post by az on 2005-08-11
Autodetection is screwy of there is an X server running.

Try booting into recovery mode and running dpkg-reconfigure xserver-xorg.  In recovery mode, there is no x server running, so it should autodetect and bring you back to the state when you first installed.

If you do not see the grub menu when you boot, hit escape and pick recovery mode.

---

