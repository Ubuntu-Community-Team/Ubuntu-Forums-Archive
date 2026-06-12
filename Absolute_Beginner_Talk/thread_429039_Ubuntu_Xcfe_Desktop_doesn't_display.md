---
title: "Ubuntu Xcfe Desktop doesn't display"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2007-04-30
The XUbuntu 6.10 desktop doesn't display where it should usually be.  The process seems to quit every time I boot it up.  Can someone please help?

---

### Post by mi_were on 2007-04-30
> **purplearcanist said:**
> The XUbuntu 6.10 desktop doesn't display where it should usually be.  The process seems to quit every time I boot it up.  Can someone please help?

Your discription of the problem is a little vague. Is it that Xfce does not start at all?

---

### Post by diskotek on 2007-04-30
i had a similiar problem when i was using xubuntu 6.10, and after a gooling i found out that "xfce-weather applet" caused this error. if you are using weather app on task bar, try to remove it & restart xfce panel; i2m not sure about the command but it have to something like "killall xfce-panel" [i2m not sure about the name of the application]

---

### Post by diskotek on 2007-04-30
my solution was about "disappeared xfce-panel".....

---

### Post by purplearcanist on 2007-04-30
Sorry that my description is a little vague...

I had just switched over to XCFE after GNOME was too slow (My computer is old by today's standards).   It ran perfectly. While I was on XCFE, I had accidentally clacked on a WINE program, which caused a message box appear, telling me that the xcfe-desktop program had unexpectedly quit.  Dumbfounded, I looked at the desktop (where the icons for files in the desktop folder usually are), and found no icons where there was previously icons.  When I tried to reboot it, the desktop icons still wouldn't display, and the bug reporting program started to run (I think because the xcfe-desktop program had closed again).

---

### Post by derouge on 2007-04-30
So can you clarify what are you able to do? Use your browser? Open the terminal?

---

### Post by purplearcanist on 2007-04-30
I seem to be able to do about anything but use the icons on the desktop.  Also, right clicking on the desktop does nothing.

For some reason, when I tried to take a screenshot, that didn't work either.

---

### Post by derouge on 2007-04-30
Open a terminal and type "xfdesktop" and tell me if that re-enables the desktop and menu.

---

### Post by purplearcanist on 2007-04-30
The desktop reappeared, but I also got this mesage:

** (xfdesktop:5526): CRITICAL **: xfdesktop_grid_is_free_position: assertion `row < icon_view->priv->nrows && col < icon_view->priv->ncols' failed

I wonder if it is bad, anyway, thanks a lot.:)

---

