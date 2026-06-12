---
title: "[SOLVED] Wine"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by bobbyg on 2007-12-24
Ugh!

No matter what I do Wine is still under my Applications menu.

I have tried the following commands

```

$ sudo apt-get remove wine

$ sudo apt-get remove --purge wine

```

And I have also tried using the Synaptic Package Manager doing a complete removal

Neither of those have fully removed wine from my system. I would like to completely remove it.

Anyone have advice.

---

### Post by kpkeerthi on 2007-12-24
1. Click Places -> Home. This opens nautilus
2. Press Ctrl + H to view hidden folders
3. Delete the below folders
	**/home/<username>/.local/share/applications/wine/Programs**
	**/home/<username>/.wine**

4. You may also want to right click on application menu and then edit menus. Then uncheck the wine entries, if exist.

---

### Post by CatKiller on 2007-12-24
If you want to quickly and easily make it so that you can't see the menu entries, you can right-click on the menu and untick the box from the Wine entry.

A lot of changes to the menu require that the menu be refreshed before the changes will be shown. Have you logged out and logged in since you made the changes, or run **killall gnome-panel**?

If you want the Wine menu entry to just die, delete (as root, since it's not in your Home folder) **/etc/xdg/menus/applications-merged/wine.menu**. This file references the following files, that won't get loaded without this menu, but can be removed for neatness:
[B]
/usr/share/desktop-directories/wine-wine.directory
/usr/share/desktop-directories/wine-Programs.directory
/usr/share/desktop-directories/wine-Programs-Accessories.directory[/B]

and possibly some other wine-*.directory files in that directory too.

There might also be some files in your Home folder too. I think mine are in ~.local/share/applications.

Hope this helps.

EDIT: beaten to the punch.

---

### Post by bobbyg on 2007-12-24
> **kpkeerthi said:**
> 1. Click Places -> Home. This opens nautilus
2. Press Ctrl + H to view hidden folders
3. Delete the below folders
	**/home/<username>/.local/share/applications/wine/Programs**
	**/home/<username>/.wine**

4. You may also want to right click on application menu and then edit menus. Then uncheck the wine entries, if exist.

Thanks kpkeerthi. That was a nice and easy way. All the forums I've looked to do that there were talking about doing purging and everything else. but that really did help.  And also Catkiller thanks. I do appreciate the help :D

---

