---
title: "new to ubuntu....hoping to find some help"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by chrisjm00 on 2006-04-27
ive searched the forums but havent found anything of use. what i want to do is get rid of the window animations when minimizing them. is that possible? i cant find and option anywhere...im a converting windows user and i like this interface, i just want to get rid of the animation that you get when you minimize/maximize a window. also wanted to get rid of having to see the window contents when you drag it. thanks

---

### Post by SavageBeginner on 2006-04-27
In Terminal type:```
gconf-editor
```Go to:  apps->metacity->general
Check reduced_resources
Close gconf-editor

---

### Post by chrisjm00 on 2006-04-27
awesome man, thanks

---

### Post by chrisjm00 on 2006-04-27
one more question actually..is it possible to put shortcuts to my hard drives on the desktop?

---

### Post by testube_babies on 2006-04-27
[QUOTE=chrisjm00]one more question actually..is it possible to put shortcuts to my hard drives on the desktop?[/QUOTE]

```
gconf-editor
```

go to apps -> nautilus -> desktop and check volumes_visible

---

