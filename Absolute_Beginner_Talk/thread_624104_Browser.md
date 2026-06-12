---
title: "Browser"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Taras on 2007-11-26
I have ubuntu 7.10 and firefox preinstalled, i deleated firefox and installed epiphany, but everytome wehn i do it firefox gets installed aswell, is there anyway i can just have epiphany with out having firefox too ?

---

### Post by Hospadar on 2007-11-26
probably not, epiphany uses the same rendering engine as firefox, and as such firefox is a dependency of epiphany because epiphany needs some firefox components to run.

You could try manually downloading the .deb for epiphany-browser, going in it and manually removing firefox as a dependency, but that will probably not work anyways, and it's never a good Idea to hack up packages like that, if epiphany gets an update from the repo, you'd have to redo it.

If you just want to get firefox off your menus, you can right-click the menu in your panel and remove it (right-click -> Edit Menus)

---

### Post by Taras on 2007-11-26
Cheers

---

