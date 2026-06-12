---
title: "Apearance menu acting weird"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by japtar10101 on 2007-10-29
Hey all!  I've upgraded from Feisty to Gutsy, and I see what a great idea making font, background, and Compiz preference into one single menu, but for some reason, I can't change any of them!  When I try to click on the tab to visual effect, nothing happens.  Both Background tab, Font, and user interface yeild the same result.  In fact, I can't even click customize, delete and install button either!  I can only change to a preset theme, and that for some reason causes massive lag on the system.  What's going on?  Is it because I have an ATI graphics card that's causing all this mischief?

Thanks for the info.  I didn't want to report this as a bug yet.

Edit:  It turns out that the problem only resides in GNOME interface.  I've tried it out in KDE, and everything works fine.

---

### Post by rudeboyskunk on 2007-10-30
This is a bug in Gnome, I have the same problem.

Pooh.

---

### Post by japtar10101 on 2007-10-30
> **rudeboyskunk said:**
> This is a bug in Gnome, I have the same problem.

Pooh.

Wooo.  Ouch.:(

---

### Post by sktrad_ on 2007-10-30
Try to run this command in the console (konsole or gnome-terminal):

sudo apt-get remove gtk-qt-engine

or:

sudo apt-get remove gtk2-engines-gtk-qt

(Have a read at the package description to know what You will be missing)

---

