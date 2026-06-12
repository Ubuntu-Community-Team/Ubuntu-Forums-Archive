---
title: "[SOLVED] Trash icon is gone.."
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2008-02-18
When i go to place a new trash, i get this..

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

---

### Post by geo909 on 2008-02-18
Try this:

Go to Applications->System Tools
If you see "Configuration Editor" Click on it. If you don't you have to make it appear:
Right click on ""Applications" and choose "Edit Menus"
From the menu on the left choose "System Tools", tick the "Configuration Editor" and close the menu.
Ok, now you can open configuration editor from the menu.

Choose "apps"->"nautilus"->"desktop" and tick the "trash_icon_visible".

Tell me if it appears now.

      Cheers

---

### Post by LostMagix on 2008-02-18
That did it, thank you very much!

---

### Post by Andavane on 2008-02-25
> **geo909 said:**
> Try this:

Go to Applications->System Tools
If you see "Configuration Editor" Click on it. If you don't you have to make it appear:
Right click on ""Applications" and choose "Edit Menus"
From the menu on the left choose "System Tools", tick the "Configuration Editor" and close the menu.
Ok, now you can open configuration editor from the menu.

Choose "apps"->"nautilus"->"desktop" and tick the "trash_icon_visible".

Tell me if it appears now.

      Cheers
Can I squeeze in another question:
If "Lock to Panel" isn't selected, does this make the disappearance of the icon more likely?
Is it wise to keep "Lock to Panel" selected?
Regards
John

---

### Post by crf on 2008-02-26
Lock to panel means that you can't pick it up with your mouse and drag it somewhere else. It's stuck where it is. I think it is handy to keep it, and most other panel items, locked.

I don't know if it makes it more likely or not to disappear, but I'd guess it has no effect at all.

---

