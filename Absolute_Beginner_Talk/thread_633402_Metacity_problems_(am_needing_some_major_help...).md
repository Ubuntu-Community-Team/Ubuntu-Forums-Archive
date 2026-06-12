---
title: "Metacity problems (am needing some major help...)"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Dr.Suse on 2007-12-06
i have recently made the switch from windows and i am loving xubuntu. after some usage the windows titlebar disapeared. i googled for some help and discovered running $ metacity brought the window title bar and the minimize maximize options back. ok, good. now i cant run window manager settings and everytime i run $ apt-get install it gives me a segmentation fault error.

does anyone know what to do?? there is an open terminal here that if i close it brings me back to the same missing titlebar problem. i will paste its contents here:

```

Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
cobin@laptop:~$ metacity --replace
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22005e7 (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22005e7 (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22005e7 (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22013fd (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22013fd (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22013fd (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22013fd (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22005e7 (Terminal -)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.


```

:(

---

### Post by rev.tig on 2007-12-06
Metacity is the gnome window manager,  if you are running the xbuntu your window manager is xfce.  What happens if you run xfce instead of metacity?

Not an xbutntu user so can't help that much but it might put you on the right path :)

---

