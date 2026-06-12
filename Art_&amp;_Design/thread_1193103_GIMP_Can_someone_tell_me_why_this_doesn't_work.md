---
title: "GIMP: Can someone tell me why this doesn't work?"
date: 2009-06-21
forum: Art &amp; Design
---

### Post by The Question on 2009-06-21
Hello, I am trying to edit a simple gif by making a part of it transparent.  My usual method is this:

Layers > Transparency > Add Alpha Channel.  
Choose Colour Picker and pick the color from the area you want to be transparent.  
Choose Bucket Fill tool, select Colour Erase Mode, Opacity 100%.

This works for a brand new file I create, but doesn't work for this one gif.  The alpha channel gets added fine, but when I Bucket Fill the area, it's like it is just in Normal mode.  The Erase tool will erase to the transparency, but not Bucket Fill.

Also mysteriously, some tools don't work, like Dodge/Burn and Smudge.  When I use these, they don't even come up on the Undo list.  Just nothing happens.

Anyone know what's going on?

---

### Post by Giant Speck on 2009-06-21
Image &#8594; Mode &#8594; RGB

GIF images are set to Indexed by default, which allows for a lot fewer color changes to be made to the image.  By changing the image mode to RGB, you should be able to do what you want to it.

---

### Post by mkendall on 2009-08-21
> **Giant Speck said:**
> Image &#8594; Mode &#8594; RGB

I can confirm that this resolves the issue. Thank you Giant Speck and search function.

---

### Post by Giant Speck on 2009-08-21
> **mkendall said:**
> I can confirm that this resolves the issue. Thank you Giant Speck and search function.

No problem!  I'm glad I could help.  :)

---

### Post by xabachay on 2012-01-26
> **Giant Speck said:**
> Image &#8594; Mode &#8594; RGB

GIF images are set to Indexed by default, which allows for a lot fewer color changes to be made to the image.  By changing the image mode to RGB, you should be able to do what you want to it.

Dude - I specifically joined this forum just say - THANK YOU!

I cannot begin to tell you how many times I have spent hours trying to figure out why some images just wouldn't color erase....

Thank you, thank you, thank you!

---

