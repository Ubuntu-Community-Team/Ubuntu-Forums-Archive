---
title: "Screensavers."
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-06-21
For some reason I have to start the XScreenSaver daemon everytime I start my PC for screensavers to work, I've tried starting it and logging off while saving the session, but that doesn't work, anyways to autostart the daemon?

---

### Post by clparker on 2006-06-21
hmm, how odd...anything else you can think of?

---

### Post by Just4 on 2006-06-21
No, I've been messing around with it for a day or so, its never worked right I just never gave much attention to it until today (I like locking my PC while I'm away from it so other people can't use it.) and realised my screensaver daemon wasn't running (I usually don't use screensavers and just have the monitor power-down.)

---

### Post by Brunellus on 2006-06-21
Xscreensaver is now an orphaned package (the maintainer has ceased to maintain it).  The replacement in GNOME is gnome-screensaver.

---

### Post by Anduu on 2006-06-21
To get xscreensaver to start at login add:

```
xscreensaver -nosplash 
```
to your startup entries in session properties.

---

