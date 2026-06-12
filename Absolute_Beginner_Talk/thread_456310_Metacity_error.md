---
title: "Metacity error?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-05-27
Sometimes i dont get my windows decoration and i type metacity and it is back again? but it gives an error does anybody know how toi fix this?

> Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


---

### Post by tippit78 on 2007-05-29
Open up gconf-editor and go to schemas/apps/metacity/window_keybindings/toggle_shaded

It's value should be <schema> 

At least that's what it says in my registry, and metacity seems to be working. ;)

---

