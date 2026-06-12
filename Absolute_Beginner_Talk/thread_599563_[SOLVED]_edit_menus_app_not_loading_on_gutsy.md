---
title: "[SOLVED] edit menus app not loading on gutsy"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-11-01
I can't get access to the edit menus applet from right-clicking on the menu and selecting edit menus. Is this a bug in gutsy? It worked when I was still on the older fiesty release....

---

### Post by haldean on 2007-11-01
Try running 
```
alacarte
```
or going to System -> Preferences -> Main Menu
and seeing if those work.

---

### Post by noorez on 2007-11-01
this is the result of the command:

/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/noorez/.config/menus/applications.menu'

System-Prerences->Main Menu doesn't work.

---

### Post by haldean on 2007-11-01
try running ```
chown {username} /home/noorez/.config/menus/applications.menu
chmod u+rw  /home/noorez/.config/menus/applications.menu
```

and if that doesn't work, try doing a "Complete Removal" of the Alacarte package in Synaptic or Adept, then reinstalling, and see if it keeps the same thing up.

---

### Post by noorez on 2007-11-03
Ok.

Changing the permissions worked. But I'm wondering why something like that has root ownership rather then user ownership? Is this a bug in this release?

---

### Post by haldean on 2007-11-04
Haven't seen that bug before (although that doesn't mean that other people don't have it). I guess you're just lucky :D

---

### Post by noorez on 2007-11-04
Hmmm....

Another question then.... would any configuration files such as the one I had to fix or similar ever belong to root then? or should they all belong to be?

---

### Post by noorez on 2007-11-04
Hmmm....

Another question then.... would any configuration files such as the one I had to fix or similar ever belong to root then? or should they all belong to me?

---

### Post by haldean on 2007-11-05
For configuration files which are stored in your home folder, they should all be owned by you. Most system configuration files (stored in /etc) will be owned by root (or a daemon user) but everything in your home belongs to you (or should!).

---

