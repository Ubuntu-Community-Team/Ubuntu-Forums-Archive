---
title: "Edit menu in Xubuntu?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by qix on 2007-06-08
How do I edit the menulist in Xubuntu? When I go to Settings -> Menu Editor, I can just see that it includes an 'external menu'. Where do I edit that?

---

### Post by qix on 2007-06-10
Bump...

---

### Post by ugm6hr on 2007-06-10
Haven't tried it, but:

[http://ubuntuforums.org/showthread.php?t=421973](http://ubuntuforums.org/showthread.php?t=421973)

---

### Post by qix on 2007-06-10
Sorry it doesn't help me. It's the xfce menu that is also editable via the menu interface. It does an 'include' of another menu (which is kind'a the main part of it). It is the menu that it includes that I want to edit.

---

### Post by imon9 on 2007-06-10
Hi,

just to inform you this:
the application menu that is automaticaly updatd whenever you install a new apps is "really" automatic..

to make things short, there is no simple GUI to edit it in Xubuntu (as compare to Gnome)... so, all the application menu shortcut are stored in a folder... i can;t recalled exactly now.. some thing like /usr/local/applications or /usr/share/application or something like that...

from there, you will see all the icons and shortcut to your application, which IF you delete them from the folder will "auto-magically" gone from the menu...

also, there is a setting file located in the same folder that determines what group does the applications belongs to... so go play with it if you want to..

hope this helps

---

### Post by xtang on 2007-06-10
yes, it work the way the guy before me says, although you can change the groups by editing the actual desktop files themselves (by using mousepad) and change the line where it says "Catagories=X" where X can be whatever you want like "Accessories".

---

