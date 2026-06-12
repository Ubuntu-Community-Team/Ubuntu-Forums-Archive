---
title: "How to put the standard icons on the desktop? Computer, Home, media, etc"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by CaptSaltyJack on 2007-03-05
Weird that a search for this turned up nothing relevant.  Surely someone had to have asked this...

Ubuntu 6.10 by default has a blank desktop.  How do you get the Gnome standard icons on there? (Computer, Home, etc)

---

### Post by divague on 2007-03-05
open a terminal and type:

$gconf-editor

then go to apps->nautilus->desktop

---

### Post by CaptSaltyJack on 2007-03-05
Ah, thanks!

---

### Post by deviouskoopa on 2007-03-06
thanks, i had the same question haha

---

### Post by rsambuca on 2007-03-06
Probably just quicker to drag and drop them from the main menu toolbars.

---

### Post by mcduck on 2007-03-06
> **rsambuca said:**
> Probably just quicker to drag and drop them from the main menu toolbars.

Nope, that won't work as well as using gconf-editor does. If you do it with gconf-editor the icons will always follow the icon theme you are using, and also it's not possible to accidentally remove them :)

---

### Post by rsambuca on 2007-03-06
I didn't say better, just quicker!

---

