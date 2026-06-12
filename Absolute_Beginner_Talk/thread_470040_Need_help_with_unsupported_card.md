---
title: "Need help with unsupported card?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-06-10
Finnally I've got my old PC running the way I like it. Installed Ubuntu 6.10 and Enlightenment 16, and I must say, Enlightened Gnome is very fast on this 533Mhz CPU, 256MB RAM, i810 card PC. But when I make a Gnome panel transparent or add a background image to the panel, it gets distorted and black. This is weird because E16 runs it transparency just fine with the windows and menus. It was like this before I even installed E16. Is there any way to fix it, or at least force the panel to load correctly? ;)

P.S.: Some parts of the panel go back to normal when I hover over them.

---

### Post by shae on 2007-06-10
I am not sure that the i810 supports compositing.  When that happens, then compositing is handled by the processor.  Some programs like parts of gnome can hog it when trying.  This might be the problem.  But another posibility is the theme you are using for your gtk settings.  It might not support transparency properly.  Could you perhaps post a screenshot of it?  On another computer with a i810 I had compositing working great through xfce.

---

### Post by shamushand on 2007-06-10
Here's a screenshot, I marked the flaws in red:
[URL="http://img480.imageshack.us/img480/1272/screenshottf9.png"]
 [IMG]http://img480.imageshack.us/img480/1272/screenshottf9.th.png[/IMG][/URL]

P.S.: This happens with all themes, even default Human theme.

---

### Post by shamushand on 2007-06-11
12-Hour Bump  :popcorn:

---

### Post by shamushand on 2007-06-16
One-week bump :popcorn:

---

### Post by shamushand on 2007-06-16
Fixed!!! All I did was change the color depth to 16 and rebooting. :p

---

