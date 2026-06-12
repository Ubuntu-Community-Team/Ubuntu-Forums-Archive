---
title: "bad sound in media apps, and where is Bittorrent?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by kayratorvi on 2007-02-07
Apparently BitTorrent is installed but I can't find it in the applications menu...I am only new to Ubuntu...how do I find this?
Secondly, I am getting really poor quality sound when listening to music in a variety of media players. Does anyone know a good media player for music..?

---

### Post by Maestro23 on 2007-02-07
You can open a terminal and type:

> #dpkg -L program name 

This will tell you where all files for that program are at.

---

### Post by taurus on 2007-02-07
Maybe you either need to log out and back in again or even reboot.  Then, it should be in Applications -> Internet.

---

### Post by RomeReactor on 2007-02-07
If you still can't find bittorrent, right-click on **Applications** (top left of the screen) and select **Edit Menus**; then go to internet and see if the box next to "Bit Torrent" is un-checked.

IIRC, the icon for BT was disabled by default on my system, since the graphical version of Gnome-Bittorrent only handles one file; so the easy way to use it is by just double clicking on a .torrent file and that makes the graphical version come up.

---

