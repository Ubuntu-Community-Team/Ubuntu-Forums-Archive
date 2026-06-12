---
title: "command to show desktop"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-21
im using the avant bar thing right now and am trying to figure out how to make a "show desktop" button on it. does anyone know the command to show desktop?

---

### Post by y-lee on 2008-04-21
maybe [ wmctrl ]("http://packages.ubuntu.com/gutsy/wmctrl"). You may have to install it first :)

The code below should show your desktop:


```
 wmctrl -k on
```


For more info on using wmctrl see the man page

```
man wmctrl
```

---

