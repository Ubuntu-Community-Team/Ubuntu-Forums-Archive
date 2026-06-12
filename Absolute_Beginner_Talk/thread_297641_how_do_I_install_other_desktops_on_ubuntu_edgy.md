---
title: "how do I install other desktops on ubuntu edgy ?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-11-11
I want to have gnome and KDE and other desktops available on my ubuntu edgy ?
I want to be able to choose from the sessions at login screen.

---

### Post by SRParda on 2006-11-11
install kde-base package with synaptic to enable kde seesion in options at login screen.

---

### Post by ThrobbingBrain66 on 2006-11-11
```
sudo aptitude install kubuntu-desktop
```

```
sudo aptitude install xubuntu-desktop
```

will give you kde and xfce desktops and you will be able to choose them from your sessions menu at login

---

### Post by MaximB on 2006-11-11
on the subject...
I have gnome XGL seassion.

after I install KDE I want to be able to use beryl with it.
do I need to install it all over again or there is a shortcut ?

---

### Post by Velotix on 2006-11-11
A little bit of advice to prevent you from having [the same problem I have](http://www.ubuntuforums.org/showthread.php?t=297662): Xubuntu doesn't like the kdm login manager for some reason, and uses gdm by default, as does Ubuntu and anything that uses GNOME. When you install KDE, it will prompt you to set gdm or kdm as the default, so **set it to gdm**, otherwise your Xfce sessions won't work properly.

KDE's well worth a look BTW; I'm considering a permanent switch from Xubuntu. ^^

**EDIT:** Also, [you might find this link useful](http://xwinman.org/): it gives you a list of all the window managers designed to run under X - all of these work with Ubuntu though only KDE, GNOME and Xfce are officially used. A specialised version of Ubuntu with Fluxbox is also under development, called Fluxbuntu, which may be of interest to you, though it's still under development (hence no link from me ^^).

---

