---
title: "Use parts of a theme?"
date: 2008-01-03
forum: Art &amp; Design
---

### Post by durrell on 2008-01-03
Ok I have finally gotten my panel setup exactly how I want it. Problem is, the theme with the panel settings is horrible. Well one aspect is:

[IMG]http://img.photobucket.com/albums/v157/Durrell12/Screenshot-CreateLauncher.png[/IMG]

And the entire desktop/panel:

[http://i11.tinypic.com/6nubr5d.png](http://i11.tinypic.com/6nubr5d.png) (1440x900, that's why I didn't use IMG tags)

Looks absolutely terrible. Plus the window decorator is an Aero theme, and I really don't need that. Ideally I'd like to use the Ubuntu studio theme with this exact panel. If anyone could point me in the right direction, that would be great. I'm no stranger to Linux, but when it comes to customizing GNOME..I don't really know where to begin.

Thanks in advance.

---

### Post by smartboyathome on 2008-01-03
Look for the panel background in (your-home-folder)/.themes (the folder is hidden). There should be a folder in there with your theme's name, and inside that there should be a gtk folder, which contains the panel background.

---

### Post by phenest on 2008-01-03
Open Configuration Editor and browse to:

```
/apps/panel/toplevels/panel_0/background
```
(yours may not be 'panel_0')

...and check 'fit'. Stretch seems to do the same thing.

---

### Post by durrell on 2008-01-03
That worked, but my problem still remains..I can't change the Controls away from aero-clone. If I do it makes the panel all sorts of different shades and shapes. I guess I may just have to stick with the aero. It's not a big deal, I just didn't know how complicated all the parts of the panel were. I thought they shared the same background.

Thanks guys.

---

### Post by smartboyathome on 2008-01-03
They can. You select image as your background, then when you set your new theme, the panel background stays the same.

---

