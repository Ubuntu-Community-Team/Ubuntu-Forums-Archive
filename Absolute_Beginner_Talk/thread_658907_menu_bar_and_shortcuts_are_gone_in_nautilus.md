---
title: "menu bar and shortcuts are gone in nautilus"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2008-01-05
kinda like Thunar, but i didn't install it before.

---

### Post by blueridgedog on 2008-01-05
Do you get a menu when you press ALT+V (the view menu to turn back on the main toolbar)?

---

### Post by oliviacond on 2008-01-06
nope, nothing happened

---

### Post by blueridgedog on 2008-01-06
Run:


gconf-editor

Then select 

apps -> nmautilus -> preferences

Then check start_with_toolbar

While you are there you can hunt around for the box to turn the menu back on.

---

