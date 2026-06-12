---
title: "Wierd graphical problem in console"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Ryuki_NdranC on 2008-04-14
ok i have the weirdest graphical glitch. Whenever i try to ctrl+alt+f(1-6) to go into console(non xserver) my screen get all bugged with weird color lines (not moving at all) but when i ctrl+alt+f7 it comes back to my default xserver (gnome)  in no time and without the glitch.

This same thing happends when i shutdown my computer, once the xserver is down, instead of showing all the linux bash outputs of shutdown, it just shows those weird glitches (this time moving) untill the computer turn off.

This all started to happen after i installed the ati 8-3 driver to my AMD64 HP laptop.

when i do fglrxinfo i got

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

```

compiz works fine, but its being bugging me for a while. Any clues?:confused:

Thx in advance.:)

---

### Post by estaticd on 2008-04-14
This might help you:

#

If your console screens are corrupted (you can switch with ctrl-alt-F1, but you can't see or read anything, only funny colours and patterns etc) you have the "usplash" problem in [WWW] bug #63558. Simply remove the "splash" keyword from the #kopt line in /boot/grub/menu.lst and rerun update-grub.

[https://wiki.ubuntu.com/Bugs/AtiDriver](https://wiki.ubuntu.com/Bugs/AtiDriver)

Make sure to backup your grub configuration file before saving changes.

---

### Post by Ryuki_NdranC on 2008-04-15
> **estaticd said:**
> This might help you:

#

If your console screens are corrupted (you can switch with ctrl-alt-F1, but you can't see or read anything, only funny colours and patterns etc) you have the "usplash" problem in [WWW] bug #63558. Simply remove the "splash" keyword from the #kopt line in /boot/grub/menu.lst and rerun update-grub.

[https://wiki.ubuntu.com/Bugs/AtiDriver](https://wiki.ubuntu.com/Bugs/AtiDriver)

Make sure to backup your grub configuration file before saving changes.

ohhh. i didn't knew. I know i had the laptop gusty problem when the splash screen takes years to boot the pc, so i just deleted the "quiet¨line and another line (i dont recal which), so i dont have splash screen.

thx a lot im gonna try it when i get home and im gonna post my results.

---

### Post by Ryuki_NdranC on 2008-04-19
Ok. i tryed the solution you gave me and it still doesnt work, i made a fresh install of gusty and now i can properly say when it gets screwed.

1. Fresh install of Gusty... (problem: the gusty usplash takes to long to load and when changing to console with "ctrl + alt + f(1-6)") i got a console with the wrong screen resolution, all lettes are way to big and fall out the screen)

FIX: I did "sudo nano /boot/grub/menu.lst (and deleted "ro quiet usplash" from my main boot)

2. Installed ndiswrapper and bcm4318 driver (all works fine now)

3. Installed ATI eXpress 200M driver with the "restricted driver manager" and rebooted. (problem: well the usplash screen isnt active so it boots really fast, thats not the problem, but when i try to "ctrl + alt + f(1-6)" the screen now gets all screwed with colors and patters with no console shown what so ever, same thing happens when the systems is shutting down. when i go and check the /boot/grub/menu.lst it doesn't has the ro quiet usplash line, so i dont know how to fix this problem)

Any ideas? It bugging me bad this problem, if you know anything, help plz

Thanks in advance.

---

