---
title: "[SOLVED] restore original themes and appearance"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by duruttye on 2008-03-11
I had enough!
I messed around pretty bad with themes and appearance and now it looks really funny, some characters are white etc...

Is there a way to restore the original theme of ubuntu?

thanx

---

### Post by Rocket2DMn on 2008-03-11
Try changing the name of .gnome2 in your home directory to something like .gnome2_old and restarting X would force it to generate from scratch (defaults).  If it fails or screws up the GUI, you can change it back from a tty.
May need to try with the .themes directory as well

edit: let's just try a bunch of them: .gnome, .gnome2, .gconf, .gconfd, .metacity, and .themes

---

### Post by duruttye on 2008-03-11
When you say tty, you mean to start in recovery mode, then from terminal rename that folder to the original name?

---

### Post by Rocket2DMn on 2008-03-11
That is one options, but if you get stuck outside of X, you can do CTRL+ALT+F1 to F6 to get to a similar login shell.  F7 is where X usually is, so you can get back there, too.

---

### Post by duruttye on 2008-03-11
There are 3 folders with .gnome in it:
.gnome
.gnome2
.gnome2_private

witch one is in use?

---

### Post by duruttye on 2008-03-11
I renamed the .themes folder and it has generated a new one, so now it looks okay.
Thanx

---

