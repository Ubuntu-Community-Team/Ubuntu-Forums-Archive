---
title: "[SOLVED] Need help with color replacement"
date: 2008-11-19
forum: Art &amp; Design
---

### Post by Vadi on 2008-11-19
Hi,

I need some help with a pretty basic task which for some reason I'm having difficulties with. This image: [http://www.mudlet.org/wp-content/themes/green-updown-cloud/img/main.gif](http://www.mudlet.org/wp-content/themes/green-updown-cloud/img/main.gif) needs to have the blue on the right replaced with the *#fdf7bb* color.

However when I use the color select tool, and then the bucket tool in Gimp, the blue is replaced with white, not my selected color.

Any ideas?

---

### Post by -yay- on 2008-11-19
since it's a .gif my guess would be that the colors are indexed, and therefore you don't get the color you want. Try setting the mode (Image->Mode)to RGB first, and then index it again when you save.

---

### Post by Vadi on 2008-11-19
Thank you! That was it.

---

