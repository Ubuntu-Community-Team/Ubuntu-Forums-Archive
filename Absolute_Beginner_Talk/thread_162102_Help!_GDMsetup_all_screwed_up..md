---
title: "Help! GDMsetup all screwed up."
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by chipwood10 on 2006-04-18
root@cwoodlinux:/usr/sbin# gdmsetup
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gdmsetup:8113): Gtk-WARNING **: cannot open display:
root@cwoodlinux:/usr/sbin#     

I am all confused. Half of my apps no longer work and they are all saying the same as this.

---

### Post by uteck on 2006-04-18
You need tell X to allow other users to run applications on your session.
Type "xhost +a" in a terminal loged in as you, then run gdmsetup as root.
When you are done, "xhost -a" to turn permission off, or restart X.

---

### Post by chipwood10 on 2006-04-18
No joy. same results

---

### Post by chipwood10 on 2006-04-19
Ended up I had to blow it all away and start from scratch. Somehow the xserver got screwed up and I could not recover the system. Am in process of getting everything back up and running now. Thanks for the help.

---

