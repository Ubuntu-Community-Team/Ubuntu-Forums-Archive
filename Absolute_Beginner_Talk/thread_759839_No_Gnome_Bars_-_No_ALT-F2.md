---
title: "No Gnome Bars - No ALT-F2"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-04-19
Hi
Yesterday i installed 8.04 and everything went well.
I had everything up and running without a hitch!

Anyway i updated which was a lot, 300MB worth.
I had firefox open, Pidgin and seemed fine.
But suddenly my Gnome bars dissapeared, my programs closed.
So i restarted nd still the same! ALT-F2 dosent work so i cant get a terminal up :(

Anyway have a clue why!?
Or what packages to try and reinstall vif they may have been broken in an update?

Thanks very much

---

### Post by overdrank on 2008-04-19
> **skymera said:**
> Hi
Yesterday i installed 8.04 and everything went well.
I had everything up and running without a hitch!

Anyway i updated which was a lot, 300MB worth.
I had firefox open, Pidgin and seemed fine.
But suddenly my Gnome bars dissapeared, my programs closed.
So i restarted nd still the same! ALT-F2 dosent work so i cant get a terminal up :(

Anyway have a clue why!?
Or what packages to try and reinstall vif they may have been broken in an update?

Thanks very much

HI and if you are using the nvidia graphics you may have to reconfigure your xorg.

---

### Post by prshah on 2008-04-19
> **skymera said:**
> Hi
But suddenly my Gnome bars dissapeared, my programs closed.
So i restarted nd still the same! ALT-F2 dosent work so i cant get a terminal up :(


Switch to a virtual terminal with Ctrl+Alt+F1, then login as usual. Then give the command ```
sudo /etc/init.d/gdm restart
``` and report errors if any? If no errors, switch back with Ctrl+Alt+F7, and check if everything has appeared. If not, try restarting Xserver by pressing Ctrl+Alt+Bkspace.

---

### Post by astoltz on 2008-04-19
> **skymera said:**
> Hi
But suddenly my Gnome bars dissapeared, my programs closed.
So i restarted nd still the same! ALT-F2 dosent work so i cant get a terminal up :(

Anyway have a clue why!?
Or what packages to try and reinstall vif they may have been broken in an update?
Sounds like the window manager has crashed.   Open a terminal and put in the command ```
metacity &
```

---

