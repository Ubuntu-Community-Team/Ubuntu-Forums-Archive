---
title: "Mouse Pointer invisible when new user log in"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by sharali on 2007-08-13
Hi
In Ubuntu 7.04 whenever one user logged out and a new user logged in the mouse pointer disappears. I have to restart to get back the mouse pointer. I am  using AMD 64 system. But os is 32 bit. My mouse is Microsoft USB type. Please suggest a remedy.

---

### Post by jambarama on 2007-08-13
> **sharali said:**
> Hi
In Ubuntu 7.04 whenever one user logged out and a new user logged in the mouse pointer disappears. I have to restart to get back the mouse pointer. I am  using AMD 64 system. But os is 32 bit. My mouse is Microsoft USB type. Please suggest a remedy.

Huh, that is weird.  First I guess I'd see if the mouse driver is actually dying.  Get to a terminal (you may have to switch to a tty for thsi) and type: sudo /etc/init.d/hotplug restart

If that doesn't do it, it could be an issue with X.  Try pressing ctrl-alt-backspace, which will restart X.  Is the mouse pointer back?

---

### Post by sharali on 2007-08-15
Hi
I tried both of your suggestion. But not solved the problem.
sudo /etc/init.d/hotplug restart command gives an error message"command not found".
Restarting X also will not helped. I can see icons highlighted whwnever the mouse is moved, but couldnt see the the pointer physically. By watching the highlighted icons I can work the mouse, ie without actually seeing the pointer. On restarting everything is ok again.
thank you
Ashraf

---

### Post by sharali on 2007-08-17
Hi
I got some tips from some other threads on this problem. I just managed to solve my problem by editing my /etc/X11/xorg.conf by adding the two following entries under Device section
 Option     "HWCursor"     "off"
 Option     "SWCursor"     "True"

Thanks everybody for the help in solving my problem.

---

