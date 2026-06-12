---
title: "mounted drives on desktop"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-22
how do i stop mounted drivers from appearing on the desktop?

---

### Post by PartisanEntity on 2007-06-22
Applications > System Tools > Configuration Editor

Then go to apps > nautilus > desktop and unclick **volumes_visible**

If you cannot see the Configuration Editor under System Tools then right-click on Applications and select Edit Menus, scroll down to System Tools and tick Configuration Editor to make it appear in the menu.

---

### Post by ramjet_1953 on 2007-06-22
In a terminal type this command in:

[COLOR="Red"]gconf-editor[/COLOR]

When the window opens, use the nested tree to navigate to:

[COLOR="Blue"]apps>nautilus>desktop[/COLOR]

At the bottom of the list, in the right panel, uncheck the selection [COLOR="Blue"]volumes visible[/COLOR].

Regards,
Roger :cool:

---

