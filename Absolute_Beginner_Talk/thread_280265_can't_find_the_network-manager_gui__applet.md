---
title: "can't find the network-manager gui / applet"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-19
Hi - 

I recently installed network-manager and network-manager-gnome from:

```
$ sudo aptitude install network-manager network-manager-gnome
```

I restarted my system but can't find the applet anywhere; any ideas what I need to do to locate it, add it, configure, next step, see if I did it right ?

Thanks,
Damon

---

### Post by Grey on 2006-10-19
try running nm-applet from the command line.  If that works, then you might have to manually add it to your sessions.  (System->Preferences->Sessions).  It's the far right tab, just insert the command in there.

---

### Post by thornomad on 2006-10-19
> **Grey said:**
> try running nm-applet from the command line.  If that works, then you might have to manually add it to your sessions.  (System->Preferences->Sessions).  It's the far right tab, just insert the command in there.

Oh!  I checked Sessions/Startup Pograms and it is listed as: "nm-applet --sm-disable".


And I tried running it from the command line as: nm-applet.

However, nothing happens.  Cursor moves to the next line in the terminal and then stays there.

Any other ideas ?  Thanks!

---

### Post by Grey on 2006-10-19
Sorry... for me, it just works.  I really have no idea how to troubleshoot it, and it seems to be setup properly.

---

### Post by thornomad on 2006-10-19
Yea - me either.  Smile.  Maybe it is not compatible with the D-Link DWL-650+ card I have ?

---

### Post by bcom on 2006-11-11
Try: sudo aptitude install network-manager-gnome; not sudo aptitude network-manager network-manager-gnome.

---

### Post by howlingmadhowie on 2006-11-13
i'm having exactly the same problem now. the applet was there, then i deleted something else from the taskbar, and the applet dissapeared with it. now it doesn't come back :( it is, however, still running and informs me with a pop-up message coming from the startmenu area when i'm logged in to a network.

stop the press, i found the answer. in german it's called the 'benachrichtigungsfeld' (information field) and can be added to the panel in the usual way. (right click on the panel...). this will then contain the network-manager-applet.

---

