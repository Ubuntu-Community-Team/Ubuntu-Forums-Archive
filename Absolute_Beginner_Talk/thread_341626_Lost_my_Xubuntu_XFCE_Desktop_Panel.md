---
title: "Lost my Xubuntu XFCE Desktop Panel"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2007-01-18
I lost my xubuntu XFCE Desktop Panel, top and bottom.

I tried this to solve the problem:  cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml. This didn't change anything.

I only get a blue screen with my desktop, with the files on it, but no panel on top or a "task-bar" at the bottom. :confused:

---

### Post by taurus on 2007-01-18
Try running this from a terminal!

```
xfce4-panel &
```

---

### Post by RomeReactor on 2007-01-18
Or try lowering your desktop's resolution (System-->Preferences-->Screen Resolution), apply, and change it back again to the one you were using. Maybe that'll do the trick.

---

### Post by MkfIbK7a on 2007-01-18
i think taurases scrpt will do the trick...

---

### Post by kerry_s on 2007-01-18
Press alt + F2 and type xfce4-panel

---

### Post by stroopwafel on 2007-01-19
> **kerry_s said:**
> Press alt + F2 and type xfce4-panel

This worked but I don't see the "applications" button in the top-left corner.:(

---

### Post by kerry_s on 2007-01-19
> **stroopwafel said:**
> This worked but I don't see the "applications" button in the top-left corner.:(

Right click the panel> add new item> xfce menu
you can ethier drag it straght from the window to where you want it or press the add button then move it where you want(right click move).

---

### Post by stroopwafel on 2007-02-03
Now I keep losing my Trash can (I know how to get it back though)

And worst of all: I lost all the files on my desktop. (So my desktop itself is totally blank) The panels on top and at the bottom of the desktop are showing though.

I can see my desktop files with the filemanager, but they don't show on the desktop.

What kind of bug is this, why does it keep happening to my desktop?

---

