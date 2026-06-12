---
title: "freezes during logging in"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by slimdog360 on 2007-06-13
I was stuffing around with Ubuntu yesterday, I changed a couple of things and then went into sessions and clicked 'save the current session'. Now when I try to login everything freezes as the upsplash says 'window manager' (the second icon that loads). I can log in fine in gnome safe mode or what ever it is called but not into a normal gnome session. This would tell me that I need to remove some startup script or something, but I don't know what to get rid of. 

my xsession-errors file
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "slim"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/slim-desktop:/tmp/.ICE-unix/5322
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
```


edit: I managed to fix it I think. I had to go into my /home/nick/.gnome2/sessions file and change a few things, along with changing a few other things. It was terrible but at least I learnt a few new things.

---

