---
title: "Personalized Human Icons"
date: 2007-03-26
forum: Art &amp; Design
---

### Post by kadath on 2007-03-26
I want to edit the official Human icons' color for my own personal use (not a fan of orange).

How do I go about this? I've never done anything like this before.

---

### Post by kadath on 2007-03-28
I hate to bump my own thread, but I figured, this being the art and design forum, that I'd get some tips here.

I've seen edits of the Human icons over at GNOME-Look. Where can I find the source files for the icons?

---

### Post by jlk on 2007-04-07
```
/usr/share/icons/Human/
```

The SVG versions are under /scalable
all the other sub-directories contain the PNG files

If you are going to  update the PNG files, you need to.....

```
sudo gtk-update-icon-cache –force /usr/share/icons/Human
```

---

