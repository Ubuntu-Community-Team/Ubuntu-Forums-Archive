---
title: "Exporting Bitmaps Containing Alpha Transparencies Around the Border"
date: 2007-05-24
forum: Art &amp; Design
---

### Post by mrgnash on 2007-05-24
Sorry for the overly verbose thread title, but I didn't know how else to explain it. Now that we're here though, I think an example would probably provide the best demonstration:

Here's a graphic I made in XaraLX:

[img]http://img297.imageshack.us/img297/2924/28weekspremyb6.png[/img]

Here's one I made in Inkscape:

[img]http://img408.imageshack.us/img408/2906/ajbugvy3.png[/img]

Notice the difference? The shadows around the exported PNG from Xara are perfectly preserved, whereas Inkscape has cropped them at some arbitrary point -- this is despite using approximately the same export method -- from selection/drawing. Is there some way of resolving this, or is it just another kink that hasn't been worked out in Inkscape yet?

---

### Post by hikaricore on 2007-05-25
I havn't really used Inkscape alot lately, but can't you just enlarge the canvas slightly on such images?

Or is this happening reguardless of the size of the canvas?

---

### Post by mrgnash on 2007-05-25
> **hikaricore said:**
> I havn't really used Inkscape alot lately, but can't you just enlarge the canvas slightly on such images?

Or is this happening reguardless of the size of the canvas?

Yep, it occurs no matter how big or small the canvas is -- and it should be irrelevant, because that's not what I'm exporting, only the drawing.

---

### Post by maruchan on 2007-05-25
If you export the drawing, Inkscape will crop around the largest shape it finds in the drawing. And I don't think blurring counts.

---

