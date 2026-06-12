---
title: "Feisty Fawn login freeze!!"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by CajunPirate on 2008-01-22
Installed Feisty Fawn, installed the updates, everything.
I shut down, restarted for weeks without a problem.
Last week, I flew to Missouri to visit a friend and when I turn on my computer:
Login screen runs like normal, I type my username then password and...
NOTHING!  The screen turns the background color and the mouse moves around but nothing else works!  CTRL-ALT-DEL and every button EXCEPT "screen capture" doesn't work.  None of the icons appear or anything!!  WHAT DO I DO!?!?
Real new to this, I prefer semi-detailed explanations!
Thanks for any help you can give!

---

### Post by uncannybuzzard on 2008-01-22
try booting into a terminal and running ```
dpkg-reconfigure xserver-xorg
```as root

---

### Post by staticvoid on 2008-01-22
you hit ESC at the grub boot menu and then go into recovery mode, or when your screen freezes up go to a terminal by hitting Ctrl + Alt + F1 or F2 or F3... F7 brings you back to X.

then do as uncannybuzzard suggested.

sv

---

### Post by CajunPirate on 2008-01-22
Nope, still just sits there after login.
I tried several configurations, but all with the same result.

---

