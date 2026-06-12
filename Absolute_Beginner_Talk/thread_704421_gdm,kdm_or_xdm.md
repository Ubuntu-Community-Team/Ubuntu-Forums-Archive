---
title: "gdm,kdm or xdm??"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by matey3 on 2008-02-22
what are the differences?
which is better? is there another display manager or even a GUI program ? whats X11 or what does startx do (I mean whic does it run)?

Also is there a way one could switch between these different windows? I mean without rebooting? 

thanks in advance.

---

### Post by kwilliam on 2008-02-22
gdm, kdm, and xdm are all just login managers.  All they do is display themselves once the computer is booted and let you type in your username and password, and then log you in.  It doesn't matter which you use.  You can still choose a Gnome, KDE, or XFCE session regardless of which login display manager you choose.

X11 is the "thing" that handles drawing stuff on the computer screen and intercepting keyboard and mouse commands.  It is also called X, the X Window System, or X.Org.  X must be started before you can run any graphical applications, such as the Gnome Desktop.  "startx" is the command that starts the X Window System.  However, usually a login manager will run "startgnome" or "startkde", which are more useful, because they call "startx" and then launch the desktop environment (start menu, wallpaper, etc).

I'm not sure what you mean by "switch between these different windows", but it is certainly possible to run Gnome programs and KDE programs at the same time.

---

