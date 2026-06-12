---
title: "quick fluxbox question"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-06-24
how can i lock screen or change users like in gnome?

---

### Post by bodhi.zazen on 2007-06-24
You can lock the screen with your screensaver (xscreensaver)

You can change users in a terminal with su <user> #enter password

But that I now of you can not change users like gnome.

---

### Post by jis on 2007-06-30
> **bodhi.zazen said:**
> You can lock the screen with your screensaver (xscreensaver)


But don't you have to use xscreensaver-demo to "lock screen now". In Xubuntu (Xfce) you could do it by pressing alt-ctrl-del. It that possible in fluxbox? Anyway, I found [XScreenSaver.App]("http://xscreensaverapp.sourceforge.net/"), but couldn't install it in Dapper. (./configure gave "Error: libdockapp was not found" even though I had libdockapp2 package installed from universe.)

---

### Post by bodhi.zazen on 2007-06-30
> **jis said:**
> But don't you have to use xscreensaver-demo to "lock screen now". In Xubuntu (Xfce) you could do it by pressing alt-ctrl-del. It that possible in fluxbox? Anyway, I found [XScreenSaver.App]("http://xscreensaverapp.sourceforge.net/"), but couldn't install it in Dapper. (./configure gave "Error: libdockapp was not found" even though I had libdockapp2 package installed from universe.)

Hey, that is a cool trick. I am sooo used to Ctrl-Alt-Del = reboot :p

---

### Post by diatribe on 2007-06-30
you could set a keybinding to use ctrl-alt-del to run xcreensaver-lock

---

### Post by kerry_s on 2007-06-30
sudo apt-get install xscreensaver fast-user-switch-applet

check in synaptic, im using debian and sometimes the names different.
there's also xscreensaver-gl if you want acceleration type screen savers.

---

### Post by bodhi.zazen on 2007-06-30
> **kerry_s said:**
> sudo apt-get install xscreensaver fast-user-switch-applet

check in synaptic, im using debian and sometimes the names different.
there's also xscreensaver-gl if you want acceleration type screen savers.

Kerry-s : Awesome tip , thanks.

---

### Post by jis on 2007-07-01
> **diatribe said:**
> you could set a keybinding to use ctrl-alt-del to run xcreensaver-lock

You mean xscreensaver-lock? Command not found.

---

### Post by kerry_s on 2007-07-01
oh, i forgot there's also xlockmore for locking the screen
sudo apt-get install xlockmore

keys:
Mod4 l :Exec xlock 

menu:
[exec] (Lock) {xlock}

there's also a xlockmore-gl if you want that. Mod4 is the windowkey

---

### Post by jis on 2007-07-11
kerry_s, thanks for the tip. (Also commad ```
xscreensaver-command -lock

``` does the job, if xscreensaver is running.)

You can configure xlock to have logout option, I wonder, if you could configure it to launch power management (suspend/hibernate) automatically after a delay. (I can click suspend in Xubuntu's shutdown dialog, but this is not present in fluxbox.)

BTW it would be nice to have laptop locked, when the cover is put down.

---

