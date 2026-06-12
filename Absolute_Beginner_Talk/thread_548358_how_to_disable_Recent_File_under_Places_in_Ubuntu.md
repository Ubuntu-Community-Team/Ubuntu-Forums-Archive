---
title: "how to disable Recent File under Places in Ubuntu"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-09-11
hello there

i want to disable Recent Files under places on main panel.

can somebody please tell m how to disable it. (or remove Recent Files tab all the way.)

---

### Post by asmoore82 on 2007-09-11
There is currently no official option to disable "Recent Documents" :/
A bug report has already been filed here: [https://bugs.launchpad.net/gnome-panel/+bug/30942](https://bugs.launchpad.net/gnome-panel/+bug/30942)
and a workaround is available;
in Terminal, delete the hidden file where they are stored and replace it with a folder of the same name:
```
~$ rm ~/.recently-used.xbel
~$ mkdir ~/.recently-used.xbel
```

---

### Post by Tyriel on 2007-09-19
> **asmoore82 said:**
> There is currently no official option to disable "Recent Documents" :/
A bug report has already been filed here: [https://bugs.launchpad.net/gnome-panel/+bug/30942](https://bugs.launchpad.net/gnome-panel/+bug/30942)
and a workaround is available;
in Terminal, delete the hidden file where they are stored and replace it with a folder of the same name:
```
~$ rm ~/.recently-used.xbel
~$ mkdir ~/.recently-used.xbel
```

Great tip thanks for that.

---

