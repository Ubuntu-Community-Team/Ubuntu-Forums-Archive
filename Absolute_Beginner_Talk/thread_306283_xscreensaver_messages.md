---
title: "xscreensaver messages"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by LexAevum on 2006-11-24
I followed a guide to replace gnome-screensaver with xscreensaver (well really just to disable the first and make the second run at startup and stuff) and I keep getting messages in my terminal window that say:
xscreensaver: 15:04:37: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 15:04:37: 0: for window 0x300001f (gnome-terminal / Gnome-terminal)

Could someone point me to where this is explained and what I need to do (if anything) about it?

---

### Post by 23meg on 2006-11-24
Which guide did you follow? Do you only get these when you type ```
xscreensaver
```as a command, or when it's running in the background as well?

---

### Post by LexAevum on 2006-11-24
This one:
[http://www.ubuntuforums.org/showthread.php?t=195557&highlight=xscreensaver](http://www.ubuntuforums.org/showthread.php?t=195557&highlight=xscreensaver)

And it happens all the time. If I hit xscreensaver in the terminal I get:
xscreensaver: 15:37:58: already running on display :0.0 (window 0x3800006)
 from process 16594

---

### Post by 23meg on 2006-11-24
In every active terminal window?

---

### Post by LexAevum on 2006-11-24
D'oh, no just the one window.

Well that was easier to fix than I had imagined. I just closed the terminal window that it was doing it in and opened a new one. What a noob.
Thanks Man.

---

