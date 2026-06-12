---
title: "How can I change the default icon for folders?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2008-01-18
I found a really good icon theme, the problem is they are .png files for windows icons, is there a way I can edit the icon theme in gnome so that all folder files take on this icon instead of the ones used by the theme?

---

### Post by peabody on 2008-01-19
Best resource I could find was this: [http://www.gnome.org/learn/admin-guide/2.2/ch03s05.html](http://www.gnome.org/learn/admin-guide/2.2/ch03s05.html)

Doesn't look like it's an easy road, the best suggestion I would have would be to find a custom theme on art.gnome.org which comes with custom folder icons, observe how they did the theme, and modify the gtkrc file in the theme tarball so it uses the image file you wish to use.

Windows icon files could be converted to png files (what gnome needs) by using the Gimp I believe.

---

