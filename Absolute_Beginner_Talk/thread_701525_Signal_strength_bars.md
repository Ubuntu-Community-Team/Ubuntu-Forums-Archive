---
title: "Signal strength bars"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by a1234 on 2008-02-19
Noob like to know how to put back he " signal  strength " bars back on to the panel. Accidentally deleted

---

### Post by notwen on 2008-02-19
Right click on your panel and add the Network-Manager applet.  Hope this helps. =]

---

### Post by a1234 on 2008-02-19
> **notwen said:**
> Right click on your panel and add the Network-Manager applet.  Hope this helps. =]
 Not on the list. I've tried that.

---

### Post by diablo75 on 2008-02-19
That icon is the Network Manager Applet, and can be started with the command "nm-applet --sm-disable". Try running that command from a terminal (Applications > Accessories > Terminal) or from the Run dialog (Alt+F2) to make sure it works and what the problem is if it doesn't.

It is by default set to be started when you log in by being listed in the Startup Programs under System > Preferences > Session. If it isn't there, add it, and it will hopefully startup when you log in.

---

### Post by notwen on 2008-02-19
Have you attempted to restart your session?  If I recall accurately the applet won't offer wireless until you restart/reboot.

---EDIT---
diablo75 beat me to it.  =]

---

### Post by a1234 on 2008-02-19
Network-manager is checked. ,
 terminal "nm-applet --sm-disable" run.
Reboot done
No go.

---

### Post by RxRated on 2008-02-19
Right click the top taskbar, select add to panel and select Notification Area from the list.

Steve

---

