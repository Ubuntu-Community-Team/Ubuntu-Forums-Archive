---
title: "S-Video to TV"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Tombo5150 on 2007-10-07
I have an S-Video port out and a cable to hook up to my tv. What is the keyboard shortcut (I use Feisty currently) to get the screen on the tv?

---

### Post by sc30317 on 2007-10-07
What kind of video card do you have?

If you have ATI, it is very difficult to get to work, although you can try to install the FGLRX drivers and look for the dual head option to change in your XORG

If you have a NVIDIA card, I would download the NVIDIA drivers from the site.  Install them (you must kill your X session to install them - hit CTRL+ALT+F1 to get to a terminal, type "killall gdm" to get rid of gdm, cd to the directory you d/l'ed to the driver from, and then type in sudo sh nvidia-PACKAGENAME.  You then go through that directory, and after that, you can type sudo gdm to get back to the gnome display manager.  run sudo nvidia-settings in a terminal, and you should be able to get dual head set up there!

PM me if you have any more ?s

---

### Post by Dr Small on 2007-10-07
[http://ubuntuforums.org/showthread.php?t=554095](http://ubuntuforums.org/showthread.php?t=554095)

---

### Post by Tombo5150 on 2007-10-08
I have an Intel video card.

---

