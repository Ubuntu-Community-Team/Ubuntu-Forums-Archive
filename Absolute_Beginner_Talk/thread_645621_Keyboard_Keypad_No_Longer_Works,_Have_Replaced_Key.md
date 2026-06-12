---
title: "Keyboard Keypad No Longer Works, Have Replaced Keyboard"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Patriot1776 on 2007-12-20
Something strange has started happening, the keypad on my keyboard has stopped being recognized, and I have replaced my keyboard.  It's a new PS/2 Windows-compatible keyboard, and the number keypad is not being recognized or the computer is not taking commands from it.  What is the command to run X configuration again?

---

### Post by cmnorton on 2007-12-20
Look at your X config file. Mine is in /etc/X11/xorg.conf.

Also, is this possibly a num lock key issue?

---

### Post by SunnyRabbiera on 2007-12-20
what kind of keyboard is it, is it a generic one or otherwise?

---

### Post by Patriot1776 on 2007-12-20
Brand new generic Logitech 104-key Windows keyboard is what it is.  In the xorg.conf file what should I look for?

---

### Post by cmnorton on 2007-12-20
Mea culpa. It looks like you can more easily configure the keyboard in System --> Preferences --> Keyboard --> Layouts

---

### Post by Patriot1776 on 2007-12-24
How do you get to that in KDE?  I've discovered something new:

Keypad works after entering text mode with Ctrl+Alt+F1.

---

### Post by Patriot1776 on 2007-12-26
:shock:

Just switched from KDE to GNOME, and now my numeric pad's working again!!  What the heck?!

:-?

Well, I guess I'm back to using GNOME for a good while then.

---

