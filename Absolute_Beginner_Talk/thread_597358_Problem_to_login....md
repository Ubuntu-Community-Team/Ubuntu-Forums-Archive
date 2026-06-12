---
title: "Problem to login..."
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by inter-m on 2007-10-30
After I type in my username and password it logs me in normaly... then for no reason the screen shows a black screen with lots of words and retruns me back to the login screen... Usually after trying a couple of times to login then it will act normal and let login... so I made another account and I have noticed that it does not do that with my other account... Can anyone help me please...:confused:

---

### Post by steve.horsley on 2007-10-30
It sounds like a bad setting somewhere. If you don't mind losing all of your GUI settings, you can try this:

1) log out
2) Use Ctrl-Alt-F2 to get a text login prompt. Log in as you
3) Either rename or delete the following directories:
.gconf
.gconfd
.gnome
.gnome2
.gnome2_private

Heaven only knows why gnome like to scatter their settings around like confetti.

---

### Post by inter-m on 2007-11-10
Thanx man that worked for me... but as u said I lost all my gui settings... thanx ;)

---

