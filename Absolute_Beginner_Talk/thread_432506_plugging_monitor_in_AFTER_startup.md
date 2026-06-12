---
title: "plugging monitor in AFTER startup"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by fhqwhgad on 2007-05-04
Hi,
If i plug my monitor into my computer after ubuntu allready started up, how do i get it to register it?
At the moment it just goes into power save, i'm assuming it's because ubuntu detects monitor on startup.

Isn't there a service i can simple restart?

---

### Post by spin2cool on 2007-05-04
I'm not positive that this will work, but you might try restarting the X server.  hit Ctrl-Alt-F1, login,  then type "sudo /etc/init.d/gdm restart"

---

### Post by fhqwhgad on 2007-05-04
> **spin2cool said:**
> I'm not positive that this will work, but you might try restarting the X server.  hit Ctrl-Alt-F1, login,  then type "sudo /etc/init.d/gdm restart"

Worked perfectly, thank you.

---

