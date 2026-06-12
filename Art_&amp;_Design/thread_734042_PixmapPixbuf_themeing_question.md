---
title: "Pixmap/Pixbuf themeing question?"
date: 2008-03-24
forum: Art &amp; Design
---

### Post by geoken on 2008-03-24
Does anyone know where I could find some detailed docs about the pixmap/pixbuf gtk theme engine? I'm trying to build a theme which will probably use murrine as a base, then overide various elements with pixmaps. I've downloaded a lot of pixmap based themes but I'm still left with questions about certain functions of the engine. For example, I found that it sometimes seems to blur one edge of my image while leaving the other side crisp and clear. 

If anyone knew where I could get some detailed info about the engine it would be much obliged.

---

### Post by smartboyathome on 2008-03-24
I don't know about the pixmap engine specifically, but check out the gnome theme link in my sig. :)

---

### Post by geoken on 2008-03-25
There wasn't a lot of info on the pixmap engine (mainly because the guy who wrote the doc had his own competing engine) but there was enough to answer my question.

For anyone else reading this, the fix for my problem was tweaking the 'borders' property. The border property (which accepts 4 parameters [left:Number, right:Number, top:Number, bottom:Number]) basically creates a box which defines the scaled area. It's essentialy a 9 slice scaling grid where each of the 4 lines are defined by one of the properties of the 'border'

---

### Post by szerencsefia on 2008-10-01
> **geoken said:**
> Does anyone know where I could find some detailed docs about the pixmap/pixbuf gtk theme engine? I'm trying to build a theme which will probably use murrine as a base, then overide various elements with pixmaps. I've downloaded a lot of pixmap based themes but I'm still left with questions about certain functions of the engine. For example, I found that it sometimes seems to blur one edge of my image while leaving the other side crisp and clear. 

If anyone knew where I could get some detailed info about the engine it would be much obliged.

[http://live.gnome.org/GnomeArt/Tutorials/GtkEngines/PixmapEngine](http://live.gnome.org/GnomeArt/Tutorials/GtkEngines/PixmapEngine)

---

