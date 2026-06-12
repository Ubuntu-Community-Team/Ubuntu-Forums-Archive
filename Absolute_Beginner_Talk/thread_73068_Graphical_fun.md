---
title: "Graphical fun"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-10-08
resolution greater than 1024x768 would be fun stuff.
If its doable, what do I have to do?

also, less likely but still interesting - dual / triple monitor setups. Can Ubuntu do this? ...can any distribution of Linux do this, in fact? Windows XP had impressive nativeness to multiple monitors. Now I can't be proud of that, anyone can buy parts and plug them in. To make 'em work on a Linux OS... that'd be some trick stuff.

my video card has one VGA and one DVI port... that'd be awesome, but then again I'm not sure if it'd even be functional. 

...I'm off track. Really what I want is 1600x1200 resolution for the GNOME desktop or something similarly bigger than 1024x768. Its not in the basic options so I figured I'd ask.

---

### Post by matthewv on 2005-10-08
[QUOTE=nerdman]resolution greater than 1024x768 would be fun stuff.
If its doable, what do I have to do?

also, less likely but still interesting - dual / triple monitor setups. Can Ubuntu do this? ...can any distribution of Linux do this, in fact? Windows XP had impressive nativeness to multiple monitors. Now I can't be proud of that, anyone can buy parts and plug them in. To make 'em work on a Linux OS... that'd be some trick stuff.

my video card has one VGA and one DVI port... that'd be awesome, but then again I'm not sure if it'd even be functional. 

...I'm off track. Really what I want is 1600x1200 resolution for the GNOME desktop or something similarly bigger than 1024x768. Its not in the basic options so I figured I'd ask.[/QUOTE]


Not too sure about the first part. I've had ubuntu running higher, but that was when it was autodetected (and on an lcd display). With regards to more than one moniter, look for something called xinerama. I think its installed on ubuntu by default (as libxinerama1) but I'm not sure how to set it up.

---

### Post by poofyhairguy on 2005-10-08
To fix you problem put this in a regualr terminal and answer the questions:

> sudo dpkg-reconfigure xserver-xorg


Go to as high a resolution as your monitor can stand.

And yes, Linux can do dual head. Its harder than in Windows, but when it works it works great. I use dual head all the time. If you want, the solution is here:

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

---

### Post by nerdman on 2005-10-08
Alright, its definitely workable...

but after I configure the resolutions with xserver-xorg should the new resolutions appear in my desktop resolution settings? still 1024x768 is my highest.

---

