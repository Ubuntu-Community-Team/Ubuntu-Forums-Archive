---
title: "Command line access?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by KiranF on 2006-05-16
Hello all,
I'm running on a laptop who's video card is essentially unsupported natively thru Ubuntu, so basically I can't get into the Desktop mode. 

Everything installed just fine, and i have no errors other than once the modules have loaded, the computer freezes at a blank screen.

I was thinking i could just go and install new drivers from the console version of Ubuntu, but i don't know how to get to it. Can someone PLEASE tell me how to get to console mode root access of Ubuntu, or even better, what i can do to try and "force" the desktop enviroment w/o any fancy graphical whatnots.

I'm using a Compaq p1510US and it has a Radeon Mobility 7500 with the latest Ubuntu installed.
Thanks!

---

### Post by confused57 on 2006-05-16
Pressing  Ctrl+Alt+F1 should get you to a text command prompt.

Type in:  sudo dpkg-reconfigure xserver-xorg

Press "enter",  type in password, press enter.

Select "vesa" video driver(or "ati", or "radeon") select your supported monitor resolutions.

Type in:   startx     

Press "enter"

I'm new at this too, but shouldn't hurt anything to try...

See this link:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by barbarian on 2006-05-16
my 5 cents:

before

you type sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm stop

after:

sudo /etc/init.d/gdm start

8)

---

### Post by KiranF on 2006-05-17
I have tried the ctrl+alt+f1 thing, but that doesn't work because the entire computer locks up right after loading the modules. I need to get straight to command prompt somehow, so i want to basically not run a GUI or anything...pure text...

---

### Post by barbarian on 2006-05-17
Try to restart in recovery mode or with live CD. 

btw,
Ctrl+Alt+F2, Ctrl+Alt+F3, Ctrl+Alt+F4, Ctrl+Alt+F5...
should lead to terminal also, and Alt+F7 - back to X.

---

### Post by KiranF on 2006-05-17
thanks, i got in...basically kept hitting ctrl+alt+f1 till it got it...i'm in desktop, now to see if i can't get the DRI drivers working...

---

### Post by stackcheese on 2006-06-09
I use to be able to access the full screen terminal (yes, i am new and do not know what it is called) with CTRL-ALT-F1-6 but now those short cuts seemed to stop working. Anyone know how I can get the full screen terminal back instead of going to.. Applicat-Acce-Ternminal?

Thanks

---

### Post by nanotube on 2006-06-09
[QUOTE=stackcheese]I use to be able to access the full screen terminal (yes, i am new and do not know what it is called) with CTRL-ALT-F1-6 but now those short cuts seemed to stop working. Anyone know how I can get the full screen terminal back instead of going to.. Applicat-Acce-Ternminal?

Thanks[/QUOTE]
well, i'm not sure how those console shortcuts would stop working... but in the meantime, you could just set a keyboard shortcut for the gnome terminal (i set mine to f12), and that should tide you over. (system>preferences>keyboard shortcuts panel if you are using gnome)

---

