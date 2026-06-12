---
title: "Change Highlight Colour"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by alsamman on 2007-12-04
I am just wondering if it is possible to change the colour my cursor highlights icons on the desktop with. If i click and hold the mouse and drag it through my desktop screen, i get a orange highlight colour but im just curious if I can change that so it fits my theme better. I am using compiz now so if I need to change it from there, please tell me:)

---

### Post by alsamman on 2007-12-04
bump

---

### Post by stealthefox on 2008-07-03
You have to use the Configuration Editor.

Applications> System Tools> Configuration Editor.

or run
```
gconf-editor
```

In the folder tree on the left, browse to: / > desktop > gnome > background.

The two keys: *primary_color* and *secondary_color* control the highlighted area and border color respectively.

The 12 digit number is hex for the color and transparency. The first six are for the color the second six are for the transparency.

To change the color simply right-click on the key you want to change, and then click *Edit Key...* in the menu box.

*Hex color values can be found online or in programs like The GIMP or Inkscape. I recommend just changing the first six digits, and don't forget to keep the # at the beginning.

---

