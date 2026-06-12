---
title: "Dia toolbox doesn't display icons"
date: 2010-07-20
forum: Art &amp; Design
---

### Post by albakry on 2010-07-20
Hi everyone,
I have installed Dia (v 0.97.1) in ubuntu 10.04, it works fine, but the toolbox doesn't display icons :(
This is a screenshot of the problem:

[CENTER][IMG]http://i26.tinypic.com/2wm4d94.jpg[/IMG]
[/CENTER]
 [IMG]http://tinypic.com/view.php?pic=2wm4d94&s=3[/IMG]
and the error message in the terminal:
```
~$ dia

progname=dia; RGBA=on

(dia:4541): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32
sys:1: GtkWarning: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed
sys:1: GtkWarning: gtk_drag_source_set_icon: assertion `GDK_IS_PIXMAP (pixmap)' failed
sys:1: GtkWarning: gdk_draw_drawable: assertion `GDK_IS_DRAWABLE (src)' failed
sys:1: GtkWarning: Attempt to draw a drawable with depth 24 to a drawable with depth 32
```Any ideas about how to fix this problem ?
Thanks in advance !

---

