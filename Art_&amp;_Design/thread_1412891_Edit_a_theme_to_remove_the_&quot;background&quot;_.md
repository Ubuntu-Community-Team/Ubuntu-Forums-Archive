---
title: "Edit a theme to remove the &quot;background&quot; color from windows etc..."
date: 2010-02-21
forum: Art &amp; Design
---

### Post by CJN on 2010-02-21
I was wondering if it was possible to edit a theme in such a way as to remove the background color from windows so that they would be completely transparent (most of the window would simply not be rendered) while preserving the text and icons. I currently use compiz to set transparency, but that makes the text, icons, other window elements transparent as well which is hard to read, and doesn't look as good as what I'm looking to achieve (IMHO).

Truly there are so many things this would fix for me that if I could just achieve it I could stop tweaking (and breaking things) for an entire day, so as to truly soak in the effect (and find something else to complain about).

The color I want to remove/make transparent is the one being moused over in the attached screenshot.

Anyway any help would be appreciated.

---

### Post by hyperdude111 on 2010-02-22
You could try to enable RGBA support. It's complicated but heres the guide [http://www.omgubuntu.co.uk/2010/02/enable-rgba-window-transparency-in.html](http://www.omgubuntu.co.uk/2010/02/enable-rgba-window-transparency-in.html)

---

### Post by mcduck on 2010-02-22
no, removing the background color would not make the window render as transparent. you'd just get the default background color (medium gray).

The tolkit used to render the windows is made to draw either a color or some bitmap image, it doesn't have any code to look what's under the window and draw that instead, and it doesn't (yet) have support for tsansparency either.

(Even with the ARGB-enabled version of GTK you can't simply *remove* a background color from somethign to make it transparent, you have to define a background color with a certain alpha value, otherwise you get the default opaque medium grey).

---

### Post by CJN on 2010-02-22
Thanks for the advice I was hoping that this wasn't the case, oh well, something for the future I guess.

---

