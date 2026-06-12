---
title: "(Pic)Global menu 'breaks' gnome panel transparency?"
date: 2009-02-24
forum: Art &amp; Design
---

### Post by OliverN on 2009-02-24
[IMG]http://farm4.static.flickr.com/3463/3307591768_af24837c7a.jpg[/IMG]

This is obviously a minor issue, but still annoying. I have no idea how to fix it. It doesn't happen when using the system theme - only when using a custom background or a solid color.

I use Aurora Borealis gtk theme and Global Menu 0.6.1678

---

### Post by smartboyathome on 2009-02-24
Yep, because the menu is still a GTK widget, not a panel widget, so unless you use the murrine ARGB patches, it won't do transparency.

---

### Post by OliverN on 2009-02-25
upgrading to global menu 0.7.3 fixed this!

thanks for your answer none the less.

---

### Post by NTolerance on 2009-02-26
I really love the configurability of Gnome panels but there are a ton of panel applets that don't work correctly with transparency or vertical panels.

---

