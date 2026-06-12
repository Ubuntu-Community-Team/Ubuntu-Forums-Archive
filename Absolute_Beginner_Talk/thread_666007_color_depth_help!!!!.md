---
title: "color depth help!!!!"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Jawsman on 2008-01-12
how do I change the color depth to, say, 256 colors???

please! I can't find it anywhere

---

### Post by szymon_g on 2008-01-12
sudo dpkg-reconfigure xserver-xorg ?

but, of course, Xwindowsystem have to be restarded

---

### Post by Jawsman on 2008-01-12
I did what you told, but didn't understand a thing

could you please be more specific?



how many bits is 256 colors?
not 24

---

### Post by szymon_g on 2008-01-12
its 8 bits (2^8 = 256)

you have to restart X's (ctr alt backspace) than login on (e.g.) tty2 (by pressing ctr+ alt+ f2) login, type

sudo killall -9 gdm (if you are using kubuntu: kdm)

than write :

sudo dpkg-reconfigure xserver-xorg and follow it. there should be a possiblility to choose 8 bits colour depth.
don't ask me how to change it easier (using gnome) ;p

---

### Post by Jawsman on 2008-01-12
hey! that did help!

I'm running my Xserver at 256 colors now!

I'd like to know now if anyone knows how to do this more simply, say, with a command or something so as to do this faster

I'm talking about switching between 256 colors and 32 bits color depth

---

### Post by szymon_g on 2008-01-12
i'me sure that there is an easier option- but i never needed to change colour deepth, so i wasn't looking for solving it.
btw, why are you switching beetween 8 and 32 bits :?

---

### Post by RomeReactor on 2008-01-12
Hi. If you have a nVidia card, run this in the terminal:
```
gksudo nvidia-settings
```
Once it pops up, go to the second option (X Server Display Configuration) and select your color depth there.

---

### Post by Jawsman on 2008-01-12
I'm trying to make 'Zoombinis Logical Journey' to work in Wine XD do you know this game?

please any idea in how to switchbetween 256 colors and 32 bits color depths essily? (not for you szymon_g, don't worry)

edit:
thanks for the help, Reactor!

---

