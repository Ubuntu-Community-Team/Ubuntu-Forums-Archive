---
title: "GIMP question"
date: 2006-06-27
forum: Art &amp; Design
---

### Post by Hanj on 2006-06-27
This might not be exacly an "ubuntu art" question, but I figured I'd ask anyway since there's probably some experienced Gimp users hanging out here.
I just decided to take up game programming again, and I use Blender to make sprites, and then fix them up with Gimp. Now, I need the parts of the sprites that are to be treated as transparent to be bright pink, ie exactly #ff00ff. When I use the fill tool in Gimp it always creates a kind of gradient around the edges - some pixels get another shade of pink. I want to be able to select an area, and then fill it (*only* the selection) with *exactly* #ff00ff. Surely this must be possible somehow?

---

### Post by CarpKing on 2006-06-27
Do you have "feather edges" and "antialiasing" enabled on the tool you use to select?  Maybe try disabling them.

---

### Post by Hanj on 2006-06-27
Thanks! Disabling feather edges was the trick! Problem solved :D

---

