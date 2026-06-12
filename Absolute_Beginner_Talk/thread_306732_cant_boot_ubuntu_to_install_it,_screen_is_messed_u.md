---
title: "cant boot ubuntu to install it, screen is messed up...."
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by chlorinekid on 2006-11-25
im trying to install ubuntu 6.10 on my desktop but i cant seem to get it to boot to the desktop.

i get the loading screen and then the monitor goes funny and just displays lots of green vertical lines all across the screen...

i think its booting up ok and is probably loading the desktop, but theres something wrong with the display/monitor so i cant actually see anything, only these lines across the screen..

ive read other posts similar to this one and they mention getting text on the screen like "error: cant load blah blah blah" but im not getting anything like that

ive tried booting in normal mode and safe graphics mode.

im currently downloading 6.06 to see if that makes any difference, have anyone got any ideas??

thanks

---

### Post by taurus on 2006-11-25
Maybe you want to use the alternate CD to install Edgy on your machine then.

---

### Post by chlorinekid on 2006-11-25
whats the alternate cd? whats the differnce???

---

### Post by taurus on 2006-11-25
The alternate CD will let you install it right away in text base instead of booting into GUI LiveCD first...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by chlorinekid on 2006-11-25
and you think that might fix the problem? do you think the problem i have will go away once its actually installed?

---

### Post by taurus on 2006-11-25
If you still experience problems with your graphic card or your monitor after you install Edgy, you can configure it again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by StormGuy on 2006-11-25
I had this same probelm.  Chances are pretty good you're using an NVIDIA card...and if not...it's still likely a driver issue.  If you are using an NVIDIA card, check out this link [http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499)

Good luck!

---

### Post by StormGuy on 2006-11-25
Oh, I forgot to add, you'll want to use a different video card for the installation (I borrowed an old one from a friend), or hit <Crtl>+<Alt>+<F1> to go into the first non-grapical server and do the installation from there, if possible.

---

### Post by utnubon on 2006-11-29
How does one install the nvidia drivers if one cannot get the bloody operating system to boot? Install a different video card??? Another joker!

---

