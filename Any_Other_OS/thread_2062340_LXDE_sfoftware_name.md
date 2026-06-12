---
title: "LXDE sfoftware name"
date: 2012-09-24
forum: Any Other OS
---

### Post by linux.convert on 2012-09-24
I cannot for the life of me find the name, the actual name you use to download with apt for the program that LXDE uses to change the wallpaper. It says "Desktop Properties" at the top but it's not the actual name, and google is worthless.

I looked in synaptic, but didn't see anything.

---

### Post by jerrrys on 2012-09-24
Google is worthless?  What about googlubuntu?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=wallpaper+changer+lxde&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=wallpaper+changer+lxde&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by lykwydchykyn on 2012-09-24
LXDE's desktop is handled by the file manager, pcmanfm, much in the way GNOME uses Nautilus to draw the desktop.

The desktop setting would be handled by pcmanfm, which should be a dependency of LXDE and therefore installed.

Are you not able to set the desktop background?

---

### Post by linux.convert on 2012-09-24
Ok, now that helps alot! I've already got PCmanFM cause I prefer it...and I got it to show the desktop properties window, but it didn't do anything.

---

### Post by lykwydchykyn on 2012-09-25
> **linux.convert said:**
> Ok, now that helps alot! I've already got PCmanFM cause I prefer it...and I got it to show the desktop properties window, but it didn't do anything.

Is it actually starting up when you log in?  Try checking your process list for pcmanfm.

---

### Post by qyot27 on 2012-09-25
PCManFM does have a command-line interface too.  Perhaps try fiddling with some of those options to see if you can get it working there?

It not responding can be due to a couple reasons.  One, that you've made LXDE switch desktop handling to the window manager (i.e. Openbox, usually): in which case, right-clicking the desktop would bring up the WM's menu instead.  Or, noting that I personally have no experience with this mode, PCManFM might be running as a daemon.  Like I mentioned, the CLI interface exposes these options so you should be able to switch back and forth on the fly.

---

