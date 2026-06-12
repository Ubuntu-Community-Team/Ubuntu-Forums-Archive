---
title: "Could use some GIMP help"
date: 2007-03-15
forum: Art &amp; Design
---

### Post by Griff on 2007-03-15
I just started using twinview instead of multiple x sessions on my monitors and am having wallpaper problems.  It looks like twinview stretches my current wall across both screens so I end up being able to see only part of the wallpaper.  I'd like to create a wallpaper from what I have by just repeating the image.  I.E. my 1280x1040 will become a 2560x1040 wall (just 2 walls side by side).  I've spent about an hour trying to figure out how to do this in gimp with no success.  Any help would be greatly appreciated.  If curious, here's the wall I'm using:

---

### Post by DirtDawg on 2007-03-15
Open your original, go:
-Select>All 
-Edit>Copy
-Select>None
-Image>Canvas Size
-Click the little chain icon so it's broken
-Change pop-up menu from pixels to percent,
-Change x to 200
-Click Resize button
-Edit>Paste
-In the Layers palette, click the new layer icon (so the pasted image is on it's own layer)
-Change to the Move tool (M)
-View>Snap to Grid
-Move the new layer to the empty side of the canvas
-Layer>Merge Down
-Save>Save As...

That should do it. There's probably a more precise way to move the new layer in a straight line on the x-axis, but with 'snap to grid on', you should be fine.

---

### Post by Griff on 2007-03-15
Awesome, that did it!  Thanks for your help!

-Griff

---

### Post by DirtDawg on 2007-03-15
> **Griff said:**
> Awesome, that did it!  Thanks for your help!

-Griff

You're welcome

---

### Post by directcharitycontribution on 2007-03-16
you can jump a step by using > open as layer>

i've just expressed a 5 piece panorama.

---

