---
title: "How can you disable emulated middle mouse click"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Fiyastone on 2007-05-23
This may well be a simple answer, but how can you disable the emulated middle mouse shortcut (when you press both the right and left mouse buttons at the same time).  I searched in a vast majority of places but maybe I was not typing the correct keywords or maybe I missed it.

From what I have read, this 'feature' is part of Linux itself.   The scroll wheel has full functionality on my computer so I am pretty sure Ubuntu can see that I have a 3-button (2 button w/ wheel) mouse.

Its a handy feature when you are using a 2-button mouse, but when you have a 3-button mouse, all it does is get in the way.

---

### Post by bodhi.zazen on 2007-05-23
Backup and open xorg.conf with an editor :

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

Look for the mouse input section

Change > Option "Emulate3Buttons" "True"

To > Option "Emulate3Buttons" "False"

Then re-start X

Ctrl-Alt-Backspace

---

### Post by userundefine on 2007-05-23
Press Alt+F2.  Type 'gksudo gedit /etc/X11/xorg.conf'.  Scroll down to your mouse config there and you should see an option like "Emulate3button" "true".  Either change it to "false" or put a # sign at the front of that line.

Then restart X after saving.

---

### Post by Fiyastone on 2007-05-23
Thank you both very much.  Works like a charm.

---

