---
title: "Where did the internet connection manager go?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Johnny K on 2007-06-15
I accidentally removed the internet connection manager (by default on the top panel to the left of the calendar. You know, the one that has the drop down list of the names of the wired and wireless connections so you can easily switch).

I can't seem to find it to bring it back. I don't see it in the "Add to panel" dialog (it's not the network manager). Any idea how I could get it back?

---

### Post by dbbolton on 2007-06-15
you can start it by running this command
```
nm-applet
```

if you want to run it at startup, go to System > Preferences > Session, and add the command to the startup programs.

---

### Post by Johnny K on 2007-06-15
> **dbbolton said:**
> you can start it by running this command
```
nm-applet
```

if you want to run it at startup, go to System > Preferences > Session, and add the command to the startup programs.

I typed *nm-applet* in the terminal. Nothing happened.
*nm-applet --sm-disable* was already in the session list. I restarted. Still not there.

**edit: It miraculously returned after I added the "Notification Area" to the panel where the network manager used to be. Very, very strange.**

---

### Post by dbbolton on 2007-06-15
that's because nm-applet sits in the system tray (or notification area). it isn't an independent panel applet like the "network manager" in the "add to panel" dialogue.

---

