---
title: "Recycle Bin"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Eddie002Fast on 2007-10-29
how do i make shortcut on my desktop with the recycle bin? :D

---

### Post by Jimmyfj on 2007-10-29
Go to Programs>Add or Remove programs>Other and install gTweakUI nautilus. This will ask you to install a few other programs as well which you simply accept.

After install go to System>Accessories>gTweakUI nautilus and you'll find several folders you can put on the desktop including the recycle bin.

---

### Post by meindian523 on 2007-10-29
Type in Terminal(Application>>Accessories>>Terminal)

```
gconf-editor
```

In the window that opens up,follow the path given below

```
/>>apps>>nautilus>>desktop
```

In the right hand side pane,check the box for trash_icon_visible

close gconf-editor

and voila!

---

### Post by meindian523 on 2007-10-29
> **Jimmyfj said:**
> Go to Programs>Add or Remove programs>Other and install gTweakUI nautilus. This will ask you to install a few other programs as well which you simply accept.

After install go to System>Accessories>gTweakUI nautilus and you'll find several folders you can put on the desktop including the recycle bin.

Why install extra stuff when we can do thru default options??

---

### Post by Jimmyfj on 2007-10-29
Could be he wanted more than just one tweak?

---

### Post by meindian523 on 2007-10-29
Point,but then he would ask for them too,right?

---

