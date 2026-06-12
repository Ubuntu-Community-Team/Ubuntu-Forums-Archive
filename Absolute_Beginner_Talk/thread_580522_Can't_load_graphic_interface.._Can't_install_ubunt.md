---
title: "Can't load graphic interface.. Can't install ubuntu :-("
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by NeMeSiS187 on 2007-10-18
Hey everyone I was just trying to install desktop 7.10 on my Lenovo Thinkpad T60 Widescreen with an X1400 video card and I'm having difficulties even getting into the graphic interface. 

It goes through the entire process of setting up keymap, drivers, clock, event manager, etc. and everything seems OK but once it starts the gnome desktop manager the screen flashes back and forth between console (which appears to be in a bigger resolution than normal) and a fuzzy graphic a few times. Then a screen comes up telling me that "The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0. Then after 2 minutes it does the same thing. 

I can't sudo into the xorg config since I haven't installed ubuntu and I don't know the default su password. Regardless, I'm hoping someone has some sort of an idea as to how to fix this since this is the second straight release of Ubuntu with a bug that affects the T60 widescreen :-(. Last time I was actually able to install it and then find a fix.

Any help would be much appreciated.

---

### Post by Paul820 on 2007-10-18
Have you tried the alternate CD?

---

### Post by NeMeSiS187 on 2007-10-18
By alternate do you mean kUbuntu? If so, I don't want KDE so much as GNOME so I can show off Compiz Fusion to all my friends. However, if by alternate you mean somewhere out there is an alternate CD that might work, please kindly point me in the general direction of it so I can try that. ... Nevermind stupid question. I found it. I'll get back to you as to whether or not it works

---

### Post by Dr Small on 2007-10-18
Alternate cd, as in a text-based installer.
You can find one here:
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

Dr Small

---

### Post by blanktear on 2007-11-08
Any word on if the alternate Cd worked?  Does anyone know what the actual problem is?

---

### Post by arikkfir on 2007-11-14
This happens to me too (exactly the same symptoms) - will try the alternate CD and report back here (this evening or tomorrow).

---

### Post by arikkfir on 2007-11-14
Hi,

The alternate installer did succeed in finishing the installation, but when booting from the hard drive, the same problem happens.

Any help would be appreciated... I'm out of cards ;-)

---

### Post by WebSiteGuru on 2007-11-14
It is your video card. 

You can do **CTL + ALT +  F1** and it put you in terminal mode.

then run this command

```
sudo nano /etc/X11/xorg.conf
```

(I think that is the correct command to edit xorg.conf file.)

Edit your xorg.conf


**CTL O** to overwrite if prompt acept YES.

**CTL X** to exit

at the terminal 

```
sudo reboot
```

That should be it.

---

### Post by arikkfir on 2007-11-21
Yes, but what do I write in my xorg.conf? ;-)

---

