---
title: "Grass Icon in Applications"
date: 2007-07-08
forum: Apple PPC Users
---

### Post by captcadwallader on 2007-07-08
I used the Synaptic Package Manager to download Grass which is a GIS program.

I used Add/Remove to download QGIS.  Which is also GIS.


QGIS shows up in Applications under Education but I can't find the Grass icon anywhere in Applications.

I do a find and I can find the Grass directdories so I know it downloaded.

How do I get an Icon for Grass in Applications?

Mac Ibook  dual usb 500 mhz, 640 megs of memory, 100 gig hd

All the best.

---

### Post by 3rdalbum on 2007-07-08
What happens if you type "grass" into the terminal?

If the program opens, then that is the command you must put into a new menu item. You can go to System > Preferences > Main Menu to add new items to the menu. Put "grass" as the command to run.

If typing "grass" into the terminal tells you that the command was not found, then you should do the following:

1. Open Synaptic.
2. Do a search for "grass". When the package comes up, right-click (or rather, F12 while the mouse is over it) and go to Properties.
3. In the Installed Files tab, you will see lots of file paths. Any that have /bin/ in them (at the beginning or middle) and something after the last slash, are executables. You can copy and paste that particular file path into a new menu item.

---

