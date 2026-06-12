---
title: "Gnome SVG Render not do not the same as inkscape"
date: 2005-03-27
forum: Art &amp; Design
---

### Post by wfx on 2005-03-27
Hi,
why cant gnome corect render svg images made with inkscape?
Example this:
[http://teg.sourceforge.net/data/share/other/allisfulloflove_ubuntu.svg](http://teg.sourceforge.net/data/share/other/allisfulloflove_ubuntu.svg)
Should look like this (is indexed):
[http://teg.sourceforge.net/data/share/other/allisfulloflove_ubuntu.png](http://teg.sourceforge.net/data/share/other/allisfulloflove_ubuntu.png)

thx
wfx.

Ps: i move all my images to devianART

---

### Post by aaaantoine on 2007-10-06
I understand this is an old thread (ancient by Linux standards!), but I've noticed the same.  Gnome renders SVGs differently than Inkscape does.  This is either an error with Gnome or with Inkscape.

In particular, Gnome and Inkscape treat blurred objects differently.  I wonder which program is in the wrong...

---

### Post by adamorjames on 2007-10-07
> **aaaantoine said:**
> I understand this is an old thread (ancient by Linux standards!), but I've noticed the same.  Gnome renders SVGs differently than Inkscape does.  This is either an error with Gnome or with Inkscape.

In particular, Gnome and Inkscape treat blurred objects differently.  I wonder which program is in the wrong...

I hope it's not Inkscape :S

---

### Post by kayosiii on 2007-10-08
Yes Gnome uses librsvg for its SVG rendering - Inkscape uses its own engine. At current the inkscape engine is a little more advanced and uses a few features that librsvg can't render. Support for filters (in this case blur) is one of them.... Firefox is in the same boat (filters will be available in firefox 3)...

---

### Post by Endolith on 2009-03-30
So Firefox and Gnome both use the librsvg engine?  That's confusing, because they don't display special colors the same way.

I thought we could use [CSS2 system colors]("http://www.w3.org/TR/css3-color/#css2-system") ("highlight") to make theme icons that always match your system theme, but it only works inside Firefox.  If you click this and view it in Firefox, the folder icon will match your theme, but if you download it, it will just appear black:

[http://www.endolith.com/svgiconcolors/user-trash.svg](http://www.endolith.com/svgiconcolors/user-trash.svg)

So I guess it's the responsibility of the program that uses librsvg to get the system color and pass it to librsvg?  It doesn't work independently?

Firefox gets the colors from GTK in the [FONT=monospace]nsLookAndFeel.cpp[/FONT] file, but I'm not sure how the two are related otherwise.  It would be great if icon authors could just make one icon and have it automatically match any theme color.

---

### Post by smartboyathome on 2009-03-31
> **Endolith said:**
> So Firefox and Gnome both use the librsvg engine?  That's confusing, because they don't display special colors the same way.

I thought we could use [CSS2 system colors]("http://www.w3.org/TR/css3-color/#css2-system") ("highlight") to make theme icons that always match your system theme, but it only works inside Firefox.  If you click this and view it in Firefox, the folder icon will match your theme, but if you download it, it will just appear black:

[http://www.endolith.com/svgiconcolors/user-trash.svg](http://www.endolith.com/svgiconcolors/user-trash.svg)

So I guess it's the responsibility of the program that uses librsvg to get the system color and pass it to librsvg?  It doesn't work independently?

Firefox gets the colors from GTK in the [FONT=monospace]nsLookAndFeel.cpp[/FONT] file, but I'm not sure how the two are related otherwise.  It would be great if icon authors could just make one icon and have it automatically match any theme color.

Firefox doesn't repliceate GTK very well (it isn't GTK, it just tries to make itself blend in with GTK). That is why it looks different.

---

### Post by Endolith on 2009-03-31
> **smartboyathome said:**
> Firefox doesn't repliceate GTK very well (it isn't GTK, it just tries to make itself blend in with GTK). That is why it looks different.

Actually, it's the other way around.  Firefox gets the colors from GTK and matches the theme, but Gnome doesn't.

---

