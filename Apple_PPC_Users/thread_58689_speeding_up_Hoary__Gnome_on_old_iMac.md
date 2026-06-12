---
title: "speeding up Hoary / Gnome on old iMac"
date: 2005-08-21
forum: Apple PPC Users
---

### Post by patrickallo on 2005-08-21
In an attempt to turn an old iMac at work into a usable machine for internet and mail, I installed Hoary on it.

Due to low specs (G3 233 with 32mb RAM) it is hardly usable (except for command line, but that's not an option as I'm not the only user).

Compared to my old iMac at home (G3 350 with 230mb RAM) it totally unusable.

I already switched to the most basic theme, but it only helped a little.

Is there anything more I can do to enhance speed (except for the obvious, add more ram)??

thanks...

---

### Post by adwait on 2005-08-21
You could switch to a more light weight window manager, like IceWM or XFCE. Also, turn off any unnecessary services that may start up.

---

### Post by DJ_Max on 2005-08-21
Also, [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

---

### Post by patrickallo on 2005-08-24
I've been playing with xfce4 on my own iMac and am really happy with it.

On the "really really old iMac" with only 32mb RAM I did a server install and then

sudo apt-get install wdm x-window-system-core xfce4 mozilla-firefox synaptic

as the wiki said, but after a restart I only get a blank screen with flicking cursor, but no reaction whatsoever.

any suggestion, or should I just make a full install and then add xfce4 afterwards as I did on my home Linux-box.

---

### Post by ssam on 2005-08-27
get a bit more ram.

if you have less than about 128mb of ram then programs will get pushed out of ram, and into swap (virtual memory on the hard drive). linux will then be continually swapping data in and out of ram. hard drives are an order of magnitude slower than ram.

you really need to have enough ram to fit all your running programs to get the full speed out of a computer. dont expect to fit any graphical programs into 32mb.

if you could get 128 or 265 mb of ram from somewhere, then you will get a huge speed up.

---

