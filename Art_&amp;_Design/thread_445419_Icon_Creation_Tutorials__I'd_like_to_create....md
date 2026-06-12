---
title: "Icon Creation Tutorials?  I'd like to create..."
date: 2007-05-15
forum: Art &amp; Design
---

### Post by Gen2ly on 2007-05-15
I'd like to create a System Theme of icons for the entire desktop, but need the specific details as to preferred sizes, alpha blending, what the basic icon's are (arrows, what types of folders...).  What do I need to do to make the index.theme.

Suppose this is a lot of details I have to have. :)

I quickly glance gnome.org but couldn't located a search - they probably has some details??

As to the actually creation, I did find when I searched on yahoo and nice tutorial on HOW to [Icon Create on Gimp]("http://www.gimp.org/tutorials/Creating_Icons/").

Anyways, I was hoping someone had read a blog somewhere, or could help me.

---

### Post by kpolice on 2007-05-15
For the names just take the gnome icon theme and you will have almost every icon used in your desktop.

The size that you have to do are 16x16, 22x22, 24x24, 32x32 (optional), 48x48 and one scalable which can be the 48px icon in svg format. 

Use svg or png for your icons, with alpha blending of course.

An index.theme is just a text file. 

Some info, a little bit outdated in some parts but should be enough for a start:
[http://live.gnome.org/GnomeArt/Tutorials/IconThemes](http://live.gnome.org/GnomeArt/Tutorials/IconThemes)

Some more help
[http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines](http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines)

---

### Post by Gen2ly on 2007-05-16
Thats perfect, thanks kPolice.  Looks like to build a beginning base theme will take about 50 plus icons.  I've created icons before with Photoshop and I'm learning Gimp now (which is similiar enough.)  I have no idea how to create svgs though.  I realize .svg is a scalable vector graphic and Inkscape can create them, but I'd rather not have to learn a new program.  Is it possible to convert a png to .svg?

---

### Post by kpolice on 2007-05-16
I prefer Inkscape as it is easier to edit gradients, outlines, etc. If you have used Illustrator, Freehand or CorelDRAW it should be pretty straightforward. 

You can convert and SVG to PNG but not the other way around. If you don't want to use SVG for the scalable icons then make the scalable icon 128x128px in PNG.

---

