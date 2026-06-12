---
title: "restoring default panels"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by bigeyedphish4134 on 2007-06-05
feisty of course...

I accidentally deleted the top panel where it had "applications", "preferences", the clock, etc.

I just want to restore the panel to its default state without adding a blank one and putting back everything manually.

Thanks for the help.

---

### Post by Inxsible on 2007-06-05
well you deleted the panel, so it would be hard to get the default back without requiring any effort from you.

But you can do it too...its pretty simple. Right click on bottom panel and click add panel. then you can add all the apps you want there by right clicking and then add to panel

---

### Post by bigeyedphish4134 on 2007-06-05
thanks for the response

hmm...

i was hoping there would be some configuration file i could delete

---

### Post by komputes on 2007-12-13
You can also try this:

Alt+F2

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal type:

```
sudo debconf gnome-panel
```

Reboot and enjoy the default panels

:popcorn:

---

