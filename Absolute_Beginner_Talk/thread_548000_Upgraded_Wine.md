---
title: "Upgraded Wine"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2007-09-10
I upgraded wine from 9.33 to 9.43 and the wine config option in my Preferences is no longer there...

How to get it back?

---

### Post by diatribe on 2007-09-10
you can run winecfg from a terminal

---

### Post by yman on 2007-09-10
> **ExSuSEusr said:**
> I upgraded wine from 9.33 to 9.43 and the wine config option in my Preferences is no longer there...

How to get it back?

right click on the menu, select "edit menus". navigate to prefrences and click on "new item".
type "Wine Configuration" in the "Name" textfield.
type "winecfg" in the "Command" textfield.
type "Interface to set wine parameters" in the "Comment" textfield.
click "OK"

---

### Post by philinux on 2007-09-10
The version you installed does not put any menu items in for you :confused:. You have to do it manually.

The 9.33 in the repos does. I've no idea why so I went back to the .33 version.

---

