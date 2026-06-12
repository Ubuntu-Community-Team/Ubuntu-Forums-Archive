---
title: "Session type??"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by natman on 2008-04-11
I have installed Kubuntu 804 beta and was playing around, at one point adept asked to install Kdm-kde4 after that i no longer see the desktop, i rebooted now on the log in screen my only session types are default (terminal) and failsafe (terminal )
How do i restore a normal desktop manager?

---

### Post by Fate Reconciled on 2008-04-11
Try running startx at the terminal then downrev to KDE 3.5

Remember 8.04 is beta and KDE4 is still extremely buggy as well. Combining these two probably isn't the best idea.

---

### Post by natman on 2008-04-11
At the terminal i did, sudo startx
and get

Server is already active for display 0 If this server is no longer running remove /tmp/.X0-lock

---

### Post by prshah on 2008-04-11
> **natman said:**
> I have installed Kubuntu 804 beta and was playing around, at one point adept asked to install Kdm-kde4 after that i no longer see the desktop, i rebooted now on the log in screen my only session types are default (terminal) and failsafe (terminal )
How do i restore a normal desktop manager?

In a virtual terminal (ctrl+Alt+f1) try ```
sudo /etc/init.d/kdm restart
``` and see if it gives you an error? If it does, the content would be helpful.

---

### Post by natman on 2008-04-11
I typed that and the screen said stopping kdm flashed and returned to a login screen ( gui  login ) and still only two options Failsafe or Default(previous )= terminal again

---

### Post by prshah on 2008-04-11
> **natman said:**
> I typed that and the screen said stopping kdm flashed and returned to a login screen ( gui  login ) and still only two options Failsafe or Default(previous )= terminal again

Ok try ```
sudo /etc/init.d/kdm stop && startx
```

After a few seconds, you will be dumped to a "white" screen with an "X" cursor. Go back to Ctrl+Alt+F1 and give ```
sudo /etc/init.d/kdm start
```, then switch back with Ctrl+Alt+F7... if this doesn't work I'm out of ideas.

---

