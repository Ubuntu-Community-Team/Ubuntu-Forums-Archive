---
title: "Triple boot: Failed to start X Server"
date: 2007-07-26
forum: Apple Intel Users
---

### Post by Aemelica on 2007-07-26
I'm configuring my Macbook Pro to triple boot. I got to the Ubuntu part, pop the CD in and i get a "Failed to start the X server" message.

Is it probably just a bad CD?

---

### Post by cyberdork33 on 2007-07-26
> **Aemelica said:**
> I'm configuring my Macbook Pro to triple boot. I got to the Ubuntu part, pop the CD in and i get a "Failed to start the X server" message.

Is it probably just a bad CD?

Which Macbook Pro? Santa Rosa?
[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

---

### Post by Aemelica on 2007-07-26
nope, 15" C2D

---

### Post by cyberdork33 on 2007-07-26
> **Aemelica said:**
> nope, 15" C2D

Ok then you will need to look at what the problem is. When you get the Xorg failed message you can view the log. Look for lines that start with "(EE)".
you can get to a commandline by using CTRL+ALT+Fx where x is 1 - 6.

---

### Post by Aemelica on 2007-07-26
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

Fatal server error: no screens found.


I tried plugging my second monitor in while booting up and I got the same error message(s).

---

### Post by russo.mic on 2007-07-29
Okay, here we go.

So,  Go to a console, and plug a hardwire internet connection into the ethernet card.
type, hitting enter after each command:

sudo apt-get update

sudo apt-get install xorg-driver-fglrx

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

startx

this will get X running so you can install.  Remember, you'll have to do it again after you install, but this time, the installation will get put on the harddrive so it's not temporary.  (actually, you shouldn't have to do the aticonfig commands again, as xorg.conf should carry over, but do it anyway to make sure.

The first time after you log out of your gnome session, it might go back to the command line.  just type sudo shutdown now or sudo reboot now depending on your needs.

Good luck!  Make sure to post your results.

Russo

---

### Post by luisbg on 2007-07-29
yeap, it looks like you are using the wrong video driver (vesa).

but the no screen found means that the xorg.conf file has set the screen in a wrong place.

first check to use the ati drivers, if it still fails, check the screen location compared to any of all the tutorials out there.

luisbg

---

### Post by ronocdh on 2007-07-29
> **luisbg said:**
> yeap, it looks like you are using the wrong video driver (vesa).

but the no screen found means that the xorg.conf file has set the screen in a wrong place.

first check to use the ati drivers, if it still fails, check the screen location compared to any of all the tutorials out there.

luisbg
Russo.mic said it best. This happens with all the ATI MBPs. I think the (Nvidia-based) SRs have similar issues regarding vide compatibility, but this error is just a simple fglrx problem.

---

