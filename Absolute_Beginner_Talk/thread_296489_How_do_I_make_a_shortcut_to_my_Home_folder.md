---
title: "How do I make a shortcut to my Home folder?"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Antarctica on 2006-11-09
I remember back in Fedora Core 5, my Home folder had a shortcut on the Desktop.  I tried making a shortcut my making a launcher, but when I try to open the folder, it asks me always if I want to display or run in terminal or cancel.  How do I make a shortcut to the folder?  Thanks.

---

### Post by bulldog on 2006-11-09
ALT--F2 type gconf-editor.

Go to apps-nautilus-desktop and select what you want to see on your desktop.

---

### Post by localuser on 2006-11-09
```
nautilus --browser %U
```

I prefer mine on a panel.

---

### Post by Arevos on 2006-11-09
Perhaps the easiest way is to open up the "Places" menu, and then drag and drop the "Home Folder" link onto your desktop.

---

### Post by Antarctica on 2006-11-10
Hey thanks.  Now is there a way to put gconf-editor into the menu?  Thanks.

---

### Post by localuser on 2006-11-10
> **Antarctica said:**
> Hey thanks.  Now is there a way to put gconf-editor into the menu?  Thanks.

6.06: Applications | Accessories | Alacarte
6.10: System | Preferences | Menu Layout

From there New Menu and/or New Item

---

### Post by CatKiller on 2006-11-10
> **localuser said:**
> From there New Menu and/or New Item

Actually, I think "Configuration Editor", as it is referred to, is already in the menu - just not enabled by default. So you edit the menu as localuser says, or by right-clicking on the menu and selecting Edit Menu, find the entry for Configuration Editor, put a tick inthe box next to it, and you're done.

Personally, I find **Alt-F2** and typing **gconf-editor** to be quicker, but some people do like menus.

---

