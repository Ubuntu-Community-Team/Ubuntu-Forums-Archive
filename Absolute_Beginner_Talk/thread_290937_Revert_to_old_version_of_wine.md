---
title: "Revert to old version of wine"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by jaytek13 on 2006-11-01
How would I go about reverting back to wine 0.9.23? Is there a apt-get command I can use or will I have to install it from source?

I am wondering this because something they did it the update from 0.9.23 -> 0.9.24 messed up some things with World of Warcraft (get an error when trying to use opengl).

---

### Post by CatKiller on 2006-11-02
It depends on how you installed it. If you installed from source, then maybe - I have no idea. But if you installed it using one of the package-based tools (apt-get, aptitude, Synaptic) then you can select the Wine package in Synaptic, select Package -> Force Version... to pick the one that you want.

---

### Post by YokoZar on 2006-11-02
You can download old packages here:

[http://wine.budgetdedicated.com/archive](http://wine.budgetdedicated.com/archive)

Also, if an older package is working better than a newer one due to an app breaking, please file a regression bug report.

---

