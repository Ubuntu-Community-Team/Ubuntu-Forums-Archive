---
title: "Getting installed apps into the menu"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-05-01
Hi,
I just downloaded and installed Qt4-Designer (and using Synaptic, uninstalled Qt3-Designer)... now I can't see Qt4-Designer in the menu or anywhere. Is there something I have to do to get this program into the Applications menu - Add/Remove... doesn't seem to see it - or otherwise run it?
Thanks...
Robyn

---

### Post by johnc4510 on 2007-05-01
Robyn, right click on the drop down main menu, you should see edit menus in the list. Click on that,  when the window opens click the name of the sub catagory on the left side where you want the app to appear. When that opens in the right side, click the new item button on the right to add the new listing. You will also have to add the link to the app to make the menu item hot.

---

### Post by Robynsveil on 2007-05-01
> **johnc4510 said:**
> Robyn, right click on the drop down main menu, you should see edit menus in the list. Click on that,  when the window opens click the name of the sub category on the left side where you want the app to appear. When that opens in the right side, click the new item button on the right to add the new listing. [COLOR="Red"]You will also have to add the link to the app to make the menu item hot.[/COLOR]
Hi John,
Not sure what you meant by the above  - in the dialog, I added:
```
/usr/include/qt4/QtDesigner/QtDesigner
```
and so the thing shows up in the menu now, but when I try to run it, it gives me:
> Failed to execute child Process "/usr/include/qt4/QtDesigner/QtDesigner" (permission denied)

I did a mc as su, and chown the QtDesigner file now... and made it executable - do I need to do that with the entire contents of the folder? 

Cheers,
Robyn

---

### Post by jhunter on 2007-05-12
Go to your menu bar and select:
System -> Preferences -> Main Menu

Find your added command in the list.  Right-click on it and select properties.  Ensure that the path to the file is correct.  Use the browse button to ensure it is right.

(I had the same problem, and it was solved by fixing the path.)

---

