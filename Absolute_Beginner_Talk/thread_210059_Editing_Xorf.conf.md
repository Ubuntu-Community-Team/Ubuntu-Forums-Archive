---
title: "Editing Xorf.conf"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by tregarton on 2006-07-06
I need to edit my xorg.conf file in a text editor.  This I can find and load.  How do I edited it with Supervisior permission, therefore being able to save the file?

Thank inadvance,Rob

---

### Post by izmaelis on 2006-07-06
If I understand you correctly you must run any text editor as root. For example:
```
# sudo gedit /etc/X11/xorg.conf
```
and enter your root password.
After making your changes just save it. For X11 configuration changes to take effect you must restart X11.

---

### Post by lordlollo on 2006-07-06
... by the way, if you are not a super-expert (and probably even if you are...) remeber that it is always better to have a xorg.conf backup...

```
sudo cp /etc/X11/xorg.conf /etx/X11/xorg.conf.bak
```

and enter your root password when asked.

Bye

---

### Post by taurus on 2006-07-06
[QUOTE=lordlollo]
```
sudo cp /etc/X11/xorg.conf /etx/X11/xorg.conf.bak
```
[/QUOTE]
Check your typo...

---

