---
title: "Problems Installing Ubuntu On iMac G3"
date: 2006-08-26
forum: Apple PPC Users
---

### Post by Warcrafter on 2006-08-26
I decided to install Ubuntu on my old iMac G3 because I don't use it. During the first installation it seemed that everything was going fine but then once Power Managment loaded The screen went completely black.  I left it running all night hoping that it would load the installer but the screen just stayed black.  What could be the problem and how do I fix it.

---

### Post by sersetto on 2006-08-26
On my Imac G3 the screen went black for a bad configuration of X-window.
If this is your problem then:

1) press ctrl+option+F1 to get to a command line
2) type "sudo killall gdm" to kill x-window
3) type "sudo nano -w /etc/X11/xorg.conf" to open the xorg configuration file
4) look in this file for the lines
         Horizontal Sync ................
         Vertical Sync ...............
 The correct value for Horizon Sync are 60 60
 The correct value for Vertical Sync are 43 117
4) save the changes (Ctrl+x)
5) type "sudo /etc/init.d/gdm restart" to restart. x-window now it should work

Hope it helps.

P.S.: However you might have problems if you want to connect to internet with a dial-up proble (see my post :()

P.P.S: I found that Xubuntu live CD is muche better if you have small (198M) ram, in the sense that the normal Ubuntu LiveCD (with Gnome) is terribly slow: you click Install and takes for ever for something to change. Xubuntu is really "fast".

---

