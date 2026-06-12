---
title: "Scribus - could not wrap text around image"
date: 2008-08-31
forum: Art &amp; Design
---

### Post by komputes on 2008-08-31
I followed the instructions on the scribus wiki but was unable to wrap text around image.

 [http://wiki.scribus.net/index.php/How_to_wrap_text_around_frames_or_images](http://wiki.scribus.net/index.php/How_to_wrap_text_around_frames_or_images)

Do these instructions work for anyone else?

---

### Post by eternal_fizzer on 2008-09-09
I'm working in OpenSUSE, but had similar problems. I found that I made 2 errors.

1. I assumed the text box could "see" the shape in my background graphic, and forgot it was actually just a big square with a shape on it (imported from Inkscape), so I need to make a shape in Scribus - transparency doesn't change the image shape either. You can make a shape (called the Contour Line) within an image by editing in Properties > Shape > Edit Shape. In the Nodes dialog, click "Edit Contour Line", then "move nodes" (top left icon) and drag the blue corner nodes around, or add more nodes. This creates a contour so when you are back in Properties, you click "Text Flows Around Frame" AND "Use Contour Line".

2. This feature only works if the image is at least one level above the text that you want to wrap (ie text in level 2 will wrap around image in level 3 or higher). Change the level in Properties > X,Y,Z

Hope this helps!

> **komputes said:**
> I followed the instructions on the scribus wiki but was unable to wrap text around image.

[http://wiki.scribus.net/index.php/How_to_wrap_text_around_frames_or_images](http://wiki.scribus.net/index.php/How_to_wrap_text_around_frames_or_images)

Do these instructions work for anyone else?

---

### Post by komputes on 2008-09-09
Thank you so much! At first when I looked at the instructions, I was not hopeful. But then when I opened scribus, everything seemed to flow, by the way, the second step (to bring the picture up to the top layer) is accomplished by selecting the image and then then pressing the [Home] button on the keyboard (or Item > Level Raise to Top if you like menus).

Thanks again for your help!

:)

---

