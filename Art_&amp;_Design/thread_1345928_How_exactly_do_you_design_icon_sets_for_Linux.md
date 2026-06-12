---
title: "How exactly do you design icon sets for Linux?"
date: 2009-12-04
forum: Art &amp; Design
---

### Post by Cam42 on 2009-12-04
I've been wanting to do this for a while. How do I do it?

---

### Post by AJB2K3 on 2009-12-05
Well you need to be a ble to draw,
Then you need to understand how linux icons work and in what format there in,
Finially you need to understand the software needed to make them.

Last time I checked Ubuntu used .svg format so the software required to make icons is inkscape.

---

### Post by Ghost|BTFH on 2009-12-12
You can also use .png files for set sizes, so Gimp is also a possibility for creation - you just have to make your largest scale (usually 48x48) then just scale each sequential save down (32x32/24x24/22x22/16x16)

But of course, you can also have a scalable one (.svg) with Inkscape as said before.

The major difference is, if you do it all with Gimp first in the largest size possible, you can slap it into Inkscape and tell it to save the file as an .svg - best of both worlds.

Cheers,
Ghost

---

### Post by blackened on 2009-12-13
Download a few icon packages from [http://gnome-look.org]("http://gnome-look.org"), extract them and view the way they are laid out. Each will be a little different: some will use only vector images, some will use only raster images, and most will offer both.

> **Ghost|BTFH said:**
> ...The major difference is, if you do it all with Gimp first in the largest size possible, you can slap it into Inkscape and tell it to save the file as an .svg - best of both worlds...

This would have the effect of embedding a raster image inside a vector. While it would work, you would have none of the scaling benefits of the vector format, i.e. if you scaled it up past its original resolution, then it would pixelate just like any other raster image.

The correct way to accomplish a raster to vector conversion would be to manually trace the image into paths in GIMP and then save as a proper SVG or to open the raster image in Inkscape and use the auto-tracing tool to create the paths.

---

### Post by Exodist on 2009-12-13
> **Cam42 said:**
> I've been wanting to do this for a while. How do I do it?
Download the default Gnome Icon set and study it real hard. There are different Icon size sets in PNG format and a growing handful of newer SVG ones in the same file.

It takes skill like some mentioned. Mostly it takes a LOT of time.

---

### Post by Ghost|BTFH on 2009-12-13
> **blackened said:**
> Download a few icon packages from [http://gnome-look.org]("http://gnome-look.org"), extract them and view the way they are laid out.

/usr/share/icons

Does the same thing, you don't have to go anywhere.

> **blackened said:**
> This would have the effect of embedding a raster image inside a vector. While it would work, you would have none of the scaling benefits of the vector format, i.e. if you scaled it up past its original resolution, then it would pixelate just like any other raster image.

This would be why I said, you make it for the largest scaled version.  .svg for an icon can be done just fine this way, if you know you're never going beyond say, 64x64 (which would be a little insane to go beyond that).

The suggestion is just a quick down n' dirty that saves a little time and allows you to have an .svg as opposed to having 5 or more icon "sets" of fixed sizes.

I agree the "proper" procedure would be to recreate it by hand, if possible.

Cheers,
Ghost

---

### Post by blackened on 2009-12-13
> **Ghost|BTFH said:**
> /usr/share/icons

Does the same thing, you don't have to go anywhere.



Or yeah, you could do that instead. :-\"

> This would be why I said, you make it for the largest scaled version.  .svg for an icon can be done just fine this way, if you know you're never going beyond say, 64x64 (which would be a little insane to go beyond that).

The suggestion is just a quick down n' dirty that saves a little time and allows you to have an .svg as opposed to having 5 or more icon "sets" of fixed sizes.

I agree the "proper" procedure would be to recreate it by hand, if possible.

Cheers,
Ghost

You're right, it would be tremendously less time consuming to do it this way. It just feels like cheating. :D

---

