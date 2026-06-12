---
title: "VNC server problem"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by nlbs on 2007-06-12
When someone tries to views my desktop through VNC he just see's a still screenshot of my desktop (thats of at the time of starting VNC) and sometimes he see's that my cursor is moving only But the Picture does'nt change But if he moves his mouse or press keyboard button in his VNC windows My mouse also moves and teh button also gets pressed here. But I can view Other's Correctly.

---

### Post by Rocket2DMn on 2007-06-12
If he is not on your LAN, it is likely that you simply don't have adequate upload speed.  You can try setting the vncserver to a lower resolution, this might help.

---

### Post by nlbs on 2007-06-12
> **Rocket2DMn said:**
> If he is not on your LAN, it is likely that you simply don't have adequate upload speed.  You can try setting the vncserver to a lower resolution, this might help.No he is not in my LAN. How can I set VNC to a lower resolution

---

### Post by Rocket2DMn on 2007-06-12
Typically when you run vnc you aren't showing them exactly what you're viewing, you start up another session.  In your case you might just have to drop your screen resolution if you can see what he's doing while remote controlling.
If he is viewing his own session, when you boot the server you add -geometry to the command, ex:
```
vncserver -geometry 800x600
``` (or 640x480, etc)

---

