---
title: "Right Click Menu?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by 71CH on 2007-06-09
Hello
Is there anyway to right-click on the desktop and have the "start menu" pop up?

---

### Post by gerscht on 2007-06-09
Not that I know of in gnome, but if you install enlightenment as a window manager, it uses that as default.

---

### Post by bodhi.zazen on 2007-06-09
XFCE, fluxbox, Openbox, IceWM to name a few more.

+1 on enlightenment

---

### Post by 71CH on 2007-06-09
thanks for your help guys
i just tried out enlightenment and it seemed kinda cool but I was wondering if there was anything like that for gnome?

---

### Post by Outrunner on 2007-06-09
I don't think so. At least, I've never seen it done. There is in KDE though

---

### Post by ikonia on 2007-06-09
I believe you can edit the right click menu on gnome, but you have to edit some rare gconf entries by hand.

I always wanted host menus like with cde and .dtwmrc.

---

### Post by bodhi.zazen on 2007-06-09
xubuntu has xfce set up very much like gnome.

sudo aptitude install xubuntu-desktop

---

### Post by urukrama on 2007-06-09
You could also use Openbox, Fluxbox, Enlightenment, Blackbox, etc. in Gnome (instead of Metacity), and then disable Nautilus from drawing the desktop to get the right click desktop menu.

To do this, you can install the window manager of your choice and then use the command> *name of window manager you want to use* --replace. You'll also have to make some adjustments in the sessions menu or the changes will only last until you log out.

If you use the latest version of Openbox (3.4, available from the Openbox website), you'll automatically get a session 'Gnome + Openbox' in the sessions menu in GDM.

If you need more help, you'll most probably find some howtos on these forums for using each window manager with Gnome. 

If you don't want to go through all this trouble, you could just use Xfce (xubuntu), as bodhi.zazen suggested. It is quite a nice desktop environment. Good luck.

---

