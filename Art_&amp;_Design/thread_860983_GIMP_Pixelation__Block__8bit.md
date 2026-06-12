---
title: "GIMP Pixelation / Block / 8bit"
date: 2008-07-16
forum: Art &amp; Design
---

### Post by Naralas on 2008-07-16
What I am looking to do is take a logo, and have GIMP paint over it with solid blocks, to make it like an old 8bit graphic. I would love if I could do this in Inkscape to my vector image, but it does not seem to have anythin that supports that kind of plugin at all, so I guess I can content myself with converting the PNG file every time.

I have used a plugin called Photo Effects which has brick and tile modes they can apply to the image, but they are to generous about edges, which is exactly where I need them to draw the blocks, instead of just leaving it rounded.

Any ideas?

---

### Post by almsamim on 2008-07-16
can u put an example ?!

---

### Post by Naralas on 2008-07-16
Sure, here is the current logo and a picture from the first Super Mario.

I don't care about limiting it to color spectrum of NES, just about making it limited to only TWO colours (the black and the blue shade) and about making it very blocky, and on a perfect checkerboard layout. I don't want a block, and a block under it and over half a block. it needs to conform as if it were actually a 30x30 pixel image (or whatever number I end up needing to still get the point across)

I am SURE there is something out here that does this, I just can't seem to find a proper search term to find it, or figure out how to do it in GIMP. And as I said, I would prefer to do it in inkscape.

---

### Post by kid-pro-quo on 2008-07-16
Have a look at the mosaic filter in GIMP (filters > distorts > mosaic). If you turn off tile splitting (in the right hand column of checkboxes) and put neatness to maximum that might give you a start. If you play with the other settings you can tweak the final result.

Hope that helps, or at least gets you started.

---

### Post by zgornel on 2008-07-16
Another trick would be to take a picture, reduce it with a scaling factor and then resize it using nearest neighbor interpolation. You will get the pixelation effect. Then you can manually reduce the number of bits per color or whatever.

---

### Post by Naralas on 2008-07-16
> **kid-pro-quo said:**
> Have a look at the mosaic filter in GIMP (filters > distorts > mosaic). If you turn off tile splitting (in the right hand column of checkboxes) and put neatness to maximum that might give you a start. If you play with the other settings you can tweak the final result.

Hope that helps, or at least gets you started.

All that does for me is put lines through it, it does not fill out the lines where needed, and the lighting effect puts a bit of a gradient on every tile, meaning that I end up with something that has MORE colors instead of less.

It is a start I suppose if I wasn't so opposed to using the bucket fill tool for a while, but all the same, I'd prefer something built for this kind of task.

---

### Post by Naralas on 2008-07-17
Please, I really need help here

---

### Post by whiteraven on 2008-07-17
Try the Filters -> Blur -> Pixelize filter. Play around with the pixelize amount to get the best result. Then adjust the colors (might try adjusting the colors first).

---

### Post by mcduck on 2008-07-17
> **zgornel said:**
> Another trick would be to take a picture, reduce it with a scaling factor and then resize it using nearest neighbor interpolation. You will get the pixelation effect. Then you can manually reduce the number of bits per color or whatever.

This is how I'd do it. Easy and simple, no plugins or special features needed, works on every decent image manipulation program. :)

---

### Post by Xfcn on 2008-07-17
Simpler:

Image > Scale Image > 25% > Interpolation: None

Image > Scale Image > 400% > Interpolation: None

That should do it.

---

