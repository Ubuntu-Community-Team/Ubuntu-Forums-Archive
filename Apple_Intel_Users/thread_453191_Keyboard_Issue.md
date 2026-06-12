---
title: "Keyboard Issue"
date: 2007-05-24
forum: Apple Intel Users
---

### Post by erakepio on 2007-05-24
Using Ubuntu on my macbook (pure install NOT vm), and I was using VI to edit C code which I'd created, and found out backspace doesnt actually delete the letters just moves the curser back 1 space.

So now I've got no delete key when i use VI.  The backspace key works in all other apps apart from VIM and VI

---

### Post by ivesjd on 2007-05-24
Sets the lower enter key to delete. If it doesnt work, type 'xev' in terminal and get the proper keycode (you could also put it somewhere else this way).

```
#!/bin/bash
#
# Configures Macbook's right apple key to be right mouse-click
# and lower enter key to be delete.
# Install xkbset (sudo apt-get install xkbset).
# Copy this script to ${HOME}/bin/macbook (or wherever you keep your scripts)
# Make it executable:
# ( Right-click -> Properties - > Permissions -> "Allow executing file as Program"
# set GNOME to run it at login ( System -> Preferences -> Sessions 
xmodmap -e 'keycode 108 = Delete'
xkbset m
```

There is also always 'fn-delete'

***Taken from here.... [http://ubuntuforums.org/showthread.php?t=448812](http://ubuntuforums.org/showthread.php?t=448812)

---

