---
title: "Gnome processes when running Xubuntu"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by raptir on 2008-01-24
Is this normal? Here are a few that are running:

gnome-system-monitor
gconfd-2
gnome-screensaver
gnome-vfs-daemon
gnome-keyring-daemon

I guess my question is are these applications that don't have a great Xfce alternative, and thus the Gnome version is used for Xubuntu, or did these get added when I installed some application? Thanks.

---

### Post by doorknob60 on 2008-01-24
Yeah, Xubuntu uses lots of Gnome stuff, nothing to worry about.

---

### Post by raptir on 2008-01-24
Ah. Almost unfortunate. My computer's old enough that it lags while running Xubuntu. Was hoping to get rid of a few things, haha.

---

### Post by emarkd on 2008-01-24
There are even lighter-weight distributions out there.  You may want to check out [Fluxbuntu]("http://fluxbuntu.org/js.html").  It's a project aimed at having an Ubuntu system with a Fluxbox window manager.  I'm not sure how far along the project is and I've never used it, but I have used Fluxbox many times in the past and it's a great, light-weight window manager but may be a little sparse and plain for some tastes.  May be worth checking out...

---

### Post by RedSquirrel on 2008-01-25
> **raptir said:**
> Ah. Almost unfortunate. My computer's old enough that it lags while running Xubuntu. Was hoping to get rid of a few things, haha.
Try installing a command-line system and add only the things you want.

You could try the xfce4 metapackage if you want to stick with Xfce. It shouldn't install all that GNOME stuff. A light window manager would be even better: Openbox, Fluxbox, IceWM, etc.

Some ideas:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by urukrama on 2008-01-25
You can replace some of those apps with others (xscreensaver, for example). If you'd like to stick with xfce, I suggest doing a fresh install and installing the package xfce4, instead of the xubuntu-desktop package, which comes with a lot of extra (gnome) stuff. You'll have a faster Xfce.

EDIT: Or you can do as RedSquirrel also suggested, and go for Openbox or Fluxbox.

---

### Post by rosegarden78 on 2008-01-25
> **emarkd said:**
> There are even lighter-weight distributions out there.  You may want to check out [Fluxbuntu]("http://fluxbuntu.org/js.html").  It's a project aimed at having an Ubuntu system with a Fluxbox window manager.  I'm not sure how far along the project is and I've never used it, but I have used Fluxbox many times in the past and it's a great, light-weight window manager but may be a little sparse and plain for some tastes.  May be worth checking out...

I like Blackbox better than Fluxbox because I couldn't launch a terminal in Fluxbox.  Anyway, I thought all the flavors use the same kernel.  If Ubuntu lags with the Xfce manager and/or Blackbox then maybe it's not Ubuntu.  You should get acceptable performance on a CeleronM 1.1 with 512 MB and an Intel 915GM graphics card.  You can even get a cool vista osx style [here]("http://ubuntuforums.org/showthread.php?t=385981") or [here]("http://ubuntuforums.org/showthread.php?t=677959").

---

