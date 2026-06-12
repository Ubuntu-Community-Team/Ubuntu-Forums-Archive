---
title: "[SOLVED] vnc grey screen x cursor?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Deadmode on 2008-04-19
hmmm.  I'm really confused.  I tried to follow this guide, but must have taken a wrong turn somewhere?  Anyway I'm getting a grey screen pixelated screen with an x as my cursor when I attempt to vnc into my linux box.

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by kebes on 2008-04-19
Sounds like you're experiencing the problem mentioned [this thread]("http://ubuntuforums.org/showthread.php?t=232940").

The problem is that the default VNC install only loads a generic, basic window manager... whereas you probably actually want GNOME (or KDE) to load. The solution (as described in the above thread) is to edit the file "~/.vnc/xstartup", and change the last line from "x-window-manager &" to:
```
gnome-session &
```

If you want to use KDE instead of GNOME, then put "startkde &" instead.


Hope that helps.

---

### Post by Deadmode on 2008-04-19
I figured it out.  I used this how to and used x11vnc  [http://ubuntuforums.org/showthread.php?t=45565&page=6](http://ubuntuforums.org/showthread.php?t=45565&page=6) .  Now my only problem is trying to find the startup scripts or sessions in gOS linux.

---

### Post by Deadmode on 2008-04-19
Ok now I really figured it out.  I recommend using this how to.
[http://ubuntuforums.org/showthread.php?t=363236](http://ubuntuforums.org/showthread.php?t=363236)

---

