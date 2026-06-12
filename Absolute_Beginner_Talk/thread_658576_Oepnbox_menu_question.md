---
title: "Oepnbox menu question"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-01-04
okay with openbox i thought that when you open a menu it would like show a title at the top of the menu like when you right click on the desktop. well when i right click it just shows a menu with items but no title please help

---

### Post by urukrama on 2008-01-04
Menu headers are shown in Openbox' menu.xml file with the following code:

> <separator label="WHATEVER TITLE YOU WANT"/>

You can place this anywhere in the menu, just like a separator (which has the same code without the label part: <separator/>)

I am not sure what menus you refer to, though. Window menus (close, send to desktop etc.) never have a menu heading. Custom menus that you make can have one if you add the above code. Submenus can have headings if you add the above code to the top of the submenu, as the first item.

I hope this helps.

---

### Post by fedex1993 on 2008-01-05
yeah it did help alot thanks i like it better do you know how to setup transparency?

---

### Post by urukrama on 2008-01-05
You'll have to use xcompmgr and transset. I've written about that in my Openbox guide (see the link in my signature).

---

