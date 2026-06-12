---
title: "can't make gnome menu items"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by astralsin on 2007-04-20
if i go to the menu editor and try to add a menu item, it doesn't take.  does anyone know the immedate cause of this? i'm using feisty

---

### Post by Zelut on 2007-05-10
This is just a guess but it could take the menu being refreshed before those are visible.  After you add something to the menu you could try, from a terminal:

killall gnome-panel

the panel will quickly disappear and then re-appear.  Do your menus show up after that point?

---

