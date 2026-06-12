---
title: "Problem with AWN"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2008-03-29
```
cereal@cereal-desktop:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
```

and the manager wont start, ive tried reinstalling restarting xserver ect ect but nothing

---

### Post by Inxsible on 2008-03-29
did you compile AWN yourself? or did you use the repos/

---

### Post by cerealtx on 2008-03-29
synaptic

---

### Post by Inxsible on 2008-03-29
Ok try uninstalling the software completely, then also remove the user preferences from your home drive and then re-install again. That should get it going.

---

### Post by cerealtx on 2008-03-29
what are the prefrences under? i looked for .awn but did not find

---

### Post by Inxsible on 2008-03-29
its under /home/.config/awn

---

### Post by moonbeam on 2008-03-29
> **cerealtx said:**
> ```
cereal@cereal-desktop:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
```

and the manager wont start, ive tried reinstalling restarting xserver ect ect but nothing

[http://wiki.awn-project.org/FAQ#I_installed_AWN.2C_but_I_can.27t_run_awn-manager](http://wiki.awn-project.org/FAQ#I_installed_AWN.2C_but_I_can.27t_run_awn-manager).

---

