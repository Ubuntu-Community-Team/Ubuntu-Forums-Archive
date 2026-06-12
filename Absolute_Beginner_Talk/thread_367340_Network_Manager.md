---
title: "Network Manager"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by grogger13 on 2007-02-22
I just installed ndiswrapper and my dell draft n wireless 1500 mini-card.  I downloaded Network Manager for Gnome and there is no menu for it, how am i supposed to configure my laptop to use the wireless card,

---

### Post by capdog on 2007-02-22
The Network Manager appears in the "Notification Area" (same place the message appears when new updates are available)

When connected, it looks like a strengh meter, otherwise like two computer monitors one behind the other (normal network icon).

What you must do is check if you have installed the front end for network manager, it's called gnome-network-manager as well.

Try run ```
ps -A | grep nm
```

You should see "nmd" (or similar) for the backend, and "nm-applet" for frontend. Or you can just type ```
nm-applet
``` and see if it runs something.

This applet is what sits in the notification area! :)

---

