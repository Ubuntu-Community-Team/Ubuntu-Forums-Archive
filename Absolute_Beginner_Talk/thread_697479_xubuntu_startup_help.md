---
title: "xubuntu startup help"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-15
I have a few questions and a few problems regarding xubuntu startup:

1) is there a way to change the startup applications in the same way as you would o in Sessions on ubuntu?

2) when i start up, nm-applet does not appear by default. I try to ALT + F2, but the "run program" window does not appear. Later on, after a few minutes, it appears, but typing nm-applet does not bring up anything.

3)My background is just pure black and I don't know why. i tried changing it but I received a message around the lines of "gnome settings manager cannot do this becaus of a another settings manager for a different desktop environment"

---

### Post by decoherence on 2008-02-15
1) under the applications menu, under the Settings menu, select Autostarted Applications

2 & 3) your install sounds broken. Please give us more detail about your system. Is it a fresh Xubuntu install or have you converted it from Ubuntu? How did you go about installing Xubuntu?

If you converted from Ubuntu, try re-installing the xubuntu-desktop package.

Finally, I assume this is version 7.10?

---

### Post by intense.ego on 2008-02-15
Thanks for the Autostarted Applications mention. However, a netork manager is already on the list, yet none appear on my notification area. how is that?

I installed xubuntu via the terminal in ubuntu. both installations are Gutsy.

---

### Post by MasterJS on 2008-02-15
type ```
sudo apt-get install xubuntu*
``` The added asterisk will force  APT to search for everything related to Xubuntu. This might help. I've installed Xubuntu to another computer and to an external hard drive, not one problem with each.

---

### Post by intense.ego on 2008-02-16
Should I first uninstall it?

---

### Post by intense.ego on 2008-02-16
I believe the problem lies with the notification area because system monitor shows that nm-applet,amarok, ktorrent, and all other applications that usually appear in the notification are, in fact, open, but I cannot see their icons in the panel. how do I add a notification area to the panel?

This still wouldn't solve my black desktop problem though.

---

### Post by intense.ego on 2008-02-16
*bump*

---

### Post by MasterJS on 2008-02-16
do you have absolutely everything for xubuntu installed? The problem might be that somethings are missing

---

