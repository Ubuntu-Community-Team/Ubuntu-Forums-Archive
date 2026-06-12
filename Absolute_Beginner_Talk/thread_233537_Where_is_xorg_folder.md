---
title: "Where is xorg folder?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Beggar Su on 2006-08-10
Hi

I'm trying to update my intel i915 driver using [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) but when I try to install in terminal it asks for 
-------------------------------
The script will use the following Xorg directories:

Xorg Dir         : /usr/X11R6
Xorg Modules Dir : /usr/X11R6/lib/modules
Xorg Library Dir : /usr/X11R6/lib

If this is correct press ENTER, press C to change
--------------------------------

Are these the correct locations?

Trying to get tv-out to work with this graphics card.

Thanks

---

### Post by Kobalt on 2006-08-10
Hello,
seems like a good path to me...

---

### Post by Shortgeek on 2006-08-10
I can confirm two of them, but here's a maybe on the modules. Probably it's that or /usr/X11R6/lib/X11/modules. It could be something else. I can't give you an answer on that one.

P.S. It might be because I've never installed modules before, but neither /usr/X11R6/lib/X11/modules or /usr/X11R6/lib/modules exist on my machine.

---

