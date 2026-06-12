---
title: "Turning off X"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2007-04-02
The first thing someone showed me on Ubuntu after installing was a simple command to switch off X entirely and just show the command line and switch back to X instantly. (Why was that the first thing?) Does anyone know what that command is? 

I'm running Ubuntu as a server now and I'm wondering if that disabling of X would improve performance (or is X still in RAM, just being hidden?) I use X once in a while, so I don't want to login without it entirely.

---

### Post by justin whitaker on 2007-04-02
> **Ephilei said:**
> The first thing someone showed me on Ubuntu after installing was a simple command to switch off X entirely and just show the command line and switch back to X instantly. (Why was that the first thing?) Does anyone know what that command is? 

Alt-F1?

> I'm running Ubuntu as a server now and I'm wondering if that disabling of X would improve performance (or is X still in RAM, just being hidden?) I use X once in a while, so I don't want to login without it entirely.

X is still in RAM, although it is "sleeping" so it does not consume CPU cycles. So if you are using it for a production server, I would shut X off entirely, and use startx for the times you need a GUI.

---

### Post by Patrick K on 2007-04-02
Alt+ctrl+F1 thorough F6. Alt+crtl+F7 brings you back to the desktop.

---

### Post by tonyr1988 on 2007-04-02
Ctrl+Alt+F1 for Terminal
Ctrl+Alt+F7 for X

The ones in-between (F2-F6) are other consoles you can use.

If you do that, you'll still have X running. I agree with justin if you're using X less often than the command line.

---

### Post by Ephilei on 2007-04-02
That's great! Is there a terminal command for it? I'm going through SSH and VNC. ctrl+alt aren't working for me, probably because of the VNC client.

---

