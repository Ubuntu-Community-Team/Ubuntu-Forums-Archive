---
title: "X restart related bug"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by simpsonatwork on 2007-08-01
When restarting X server with ctrl-alt-backspace and accessing keyboard settings afterwards, a message appears: 
```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some
preferences may not take effect. This could indicate a problem
with Bonobo, or a non-GNOME (e.g. KDE) settings manager
may already be active and conflicting with the GNOME
settings manager.
```
Also, the keyboard layout indicator changes from "USA" to smth. like this "us          ".
Somewhere i've read it's related to bonobo-server-activation and evolution-data-server processes not killed during x restarting. Is there a way to get rid of this bug and what do these processes deal with?

---

### Post by asmoore82 on 2007-08-01
> **simpsonatwork said:**
> When restarting X server with ctrl-alt-backspace ...

:confused: how often are you doing this :shock:

the 3 finger salute X-style is more that just restarting; it's killing

the proper way to restart X is
```
~ $ sudo /etc/init.d/gdm restart
```

Also, chech that the date/time are correct on the machine.

---

### Post by simpsonatwork on 2007-08-02
Not so often as you think) 
But the problem remains no matter you Ctrl-Alt-Backspace or logout normally and then login - it eliminates only when rebooting the computer.
btw thanks for the useful piece of code)

---

