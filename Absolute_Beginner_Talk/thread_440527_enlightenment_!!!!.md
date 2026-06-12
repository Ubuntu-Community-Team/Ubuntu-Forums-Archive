---
title: "enlightenment !!!!"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by valucha on 2007-05-11
[COLOR="DarkOrchid"]i've installed enlightenment without troubles, but i changed the default theme and i can't do nothing, i cant click in the bar!!

i'm using ubuntu edgy with enlightenment E17.
Motherboard soyo sy-p4vgm, 260 ram.

The theme which i'm using an official, i mean, i've not downloaded it.

 

tanks in advance...
and sorry about my English [/COLOR]

---

### Post by cymen on 2007-05-11
Hi there, I had the same problem just yesterday! Basically, the Milky and Simply White themes (among others) don't work with the latest E17 package in their repositories. To get back to the default theme, open up a terminal and enter this:

```
enlightenment_remote -theme-set theme default.edj
```

ETA: Oh, and make sure you restart Enlightenment, obviously!

Thanks to whoever it was that originally posted that, somewhere on this forum. :D

Anyway, this page tells you the themes that do and don't work, for now: [http://www3.get-e.org/Themes/E17/](http://www3.get-e.org/Themes/E17/)

---

