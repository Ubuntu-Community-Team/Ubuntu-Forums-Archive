---
title: "gedit opens...empty file?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by IWood on 2007-10-27
I'm wanting to muck about with xorg.conf so I can see about getting Cube to work...but

sudo gedit /etc/X11/xorg.config

opens a blank window. 

I know the file's correct because a) I can open it in read mode and see what's in it and b) Ubuntu still works.

What am I missing...?

---

### Post by taurus on 2007-10-27
```
gksudo gedit /etc/X11/**xorg.conf**
```

---

### Post by dpar on 2007-10-27
I believe it's called xorg.conf, not xorg.config.

---

### Post by overdrank on 2007-10-27
> **IWood said:**
> I'm wanting to muck about with xorg.conf so I can see about getting Cube to work...but

sudo gedit /etc/X11/xorg.config

opens a blank window. 

I know the file's correct because a) I can open it in read mode and see what's in it and b) Ubuntu still works.

What am I missing...?

HI and you should use the command ```
gksudo gedit /etc/X11/xorg.conf
```
EDIT: Have to learn to type faster :)

---

### Post by Frak on 2007-10-27
.conf not .config

Also, sudo will send you to the root directories, so its good to use gksudo instead.

---

### Post by IWood on 2007-10-27
Groovy. Off to smash things. Thanks folks!!!

---

### Post by OzzyFrank on 2007-12-18
I've started having Gedit open blank unsaved files too, if I directly double click them in Nautilus. Use a command like for xorg.conf or to view sources.list, no worries. Same thing for launchers I have created for specific text files. But just try to open one directly where it is sitting, forget it! I assume this must be some sort of bug? Anyone else know more about this?

---

