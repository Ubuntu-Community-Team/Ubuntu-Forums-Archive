---
title: "Curves Are Cut Off When Rendering Bitmaps in Inkscape"
date: 2009-09-27
forum: Art &amp; Design
---

### Post by Joseph Schwenker on 2009-09-27
Hi everyone!  I have been exporting a lot of PNGS from SVGs in Inkscape, and am noticing that sometimes, a bezier curve will randomly be cut off.  This can be seen in two places in the PNG. [http://lh6.ggpht.com/_Ed2WX_IXHtg/Sx_k9oVs6WI/AAAAAAAABoM/-rb0QkLfrUY/Little%20Miss%20World%20of%20Goo.png](http://lh6.ggpht.com/_Ed2WX_IXHtg/Sx_k9oVs6WI/AAAAAAAABoM/-rb0QkLfrUY/Little%20Miss%20World%20of%20Goo.png)

You can see that on the second island, the leftmost light green bush's third curve is cut off.  You can see this again on the right side of the second island with the light brown rock's first curve, which is also cut off.  I have experienced this a lot in Inkscape, mainly with cloud patterns.  Could someone please help me?  Thanks!

---

### Post by ecmatter on 2009-09-28
If you go to View>DisplayMode>Outline you can see that both objects are being clipped by other objects.

To fix, select each item that gets clipped (just the bush and the rock in this instance -- one at a time) and go to Object>Clip>Release to release each object from the clipping paths.

---

### Post by Joseph Schwenker on 2009-09-28
Hmm... it appears that it is randomly working sometimes, and then randomly not working.  Any other things that could be causing this?  Could you try to render the SVG from the link on your computer in Inkscape?

---

### Post by Joseph Schwenker on 2009-12-09
Bump, the problem is still persisting.  Releasing it from clip (I had never set a clip in the first place) does nothing.

---

### Post by Joseph Schwenker on 2009-12-20
bump

---

### Post by Newfoundlander on 2009-12-21
Joseph, the images are not displaying.  Could you upload them again and maybe the source svg file.  I'll take a look at it and see if I can figure it.

---

### Post by Joseph Schwenker on 2009-12-23
> **Newfoundlander said:**
> Joseph, the images are not displaying.  Could you upload them again and maybe the source svg file.  I'll take a look at it and see if I can figure it.

Here is the PNG: [http://lh6.ggpht.com/_Ed2WX_IXHtg/Sx_k9oVs6WI/AAAAAAAABoM/-rb0QkLfrUY/Little%20Miss%20World%20of%20Goo.png](http://lh6.ggpht.com/_Ed2WX_IXHtg/Sx_k9oVs6WI/AAAAAAAABoM/-rb0QkLfrUY/Little%20Miss%20World%20of%20Goo.png), and the SVG should be attached to this post.

---

