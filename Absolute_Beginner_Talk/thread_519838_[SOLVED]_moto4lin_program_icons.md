---
title: "[SOLVED] moto4lin program icons"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-08-07
does anyone know where the moto4lin file is on an ubuntu feisty machine?  i'd like to replace the icons used in the toolbar with some of my own (the icons that come with the program are blurry and non-professional).  i want to make it look more like a native gnome program. 

here's a screenie.

[IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/moto4lin.png[/IMG]

---

### Post by Pragmatist on 2007-08-07
> **Niklas Schröder said:**
> does anyone know where the moto4lin file...


Here is a good way to find files.  Run this command in a terminal (wait a few minutes for it to finish):
```
sudo updatedb
```

Then run locate:
```
locate moto4lin
```

---

### Post by Niklas Schröder on 2007-08-07
eh.  it appears to be an svg hidden in the source code.  it doesn't mean enough to me to dig through all that just for icons.  thanks anyway!  :D

---

