---
title: "Change Screen Resolution"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by ledguitar on 2008-01-26
(I have seen other posts regarding this but I have not found anything that helps me)

I just switched to Ubuntu from windows xp. However, I have tried to change the screen resolution to 1440 x 900 (what I ran in xp) but my only choices are 800 x 600 and 640 x 480. I didn't understand a lot of the terminal stuff in the other posts so if any help could be directed toward a Ubuntu newbie, that would be great.

Graphics card: Nvidia 7950 GT
(not sure what else I need)

---

### Post by tranquito on 2008-01-26
You may need to activate the restricted drivers for you graphics card. If you are using gnome desktop then it should be in System>Administration>RestrictedDriversManager then just tick the box for your graphics card.

---

### Post by Rocket2DMn on 2008-01-26
First try the restricted drivers, but if that doesn't work...

you might need to reconfigure X, so we'll get you to a TTY (command line), stop gnome, do the reconfiguration, and restart gnome.  When asked about video drivers, use "nv" for the open source drivers or "nvidia" for the closed source nvidia drivers (these are the restricted drivers mentioned before).  At the resolutions page, select 1440x900 and everything less by moving with TAB and selecting with SPACEBAR
Do CTRL+ALT+F1 to get to a TTY, login, then run...
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
You will then be able to select your resolution (if it's not already set).

---

### Post by white3454 on 2008-01-26
First of all, don't give up.  Congrats on making the switch!

My laptop has Intel graphics, but try this link...

[http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver](http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver)

Don't be afraid to try a few different install options, I've reloaded my laptop like 4 times before I found the exact install I like, including packages and software.  Good Luck.

---

### Post by durdensbuddy on 2008-01-26
You may also need to add compiz-fusion if you haven't already [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)  this really helped me out.

---

