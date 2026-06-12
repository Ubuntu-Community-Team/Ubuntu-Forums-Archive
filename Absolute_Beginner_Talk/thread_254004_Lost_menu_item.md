---
title: "Lost menu item"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by zuser on 2006-09-09
Seems I lost the 'update or add applications' option from the 'Applications' menu. How do I get it back?
I looked at the menu editor but dont see it listed as a selection item.

---

### Post by timetunnel on 2006-09-10
If you open the menu editor, click on "applications" on the left side and scroll down on the right side, it should be at the bottom of the list. If it's there, make sure the check box of the item is checked. If it's not there anymore, you can create your own menu item. 

When the dialog for the new menu item appears, enter a name and description of your choice, and then the following as the command:
```
/usr/bin/gnome-app-install
```

On my system, the icon for the menu item is this one:
/usr/share/icons/gnome/48x48/apps/gnome-settings-default-applications.png

---

### Post by zuser on 2006-09-10
That did it, thanks

---

