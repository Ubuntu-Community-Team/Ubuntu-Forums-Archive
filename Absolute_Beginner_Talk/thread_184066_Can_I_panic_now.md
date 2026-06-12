---
title: "Can I panic now?"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-29
[CENTER]What
Have
I
Done?!!! ](*,) [/CENTER]

I think I uninstalled some package-or-other that I shouldn't have - to do with nautilus.
I re-installed nautilus but I think i uninstalled something else - and I can't remember what. Now, whenever I click on an icon i get the following message:

The Application "nautilus" has quit unexpectedly.

You can inform the developers of what happened to help them fix it.  Or you can restart the application right now.

Please help!!! I need the icons!!!

---

### Post by Sef on 2006-05-29
Try this:

First Open the Terminal (Applications > Accessories > Terminal)

Second type in these commands (one at a time)

a) sudo apt-get update

b) sudo aptitude install ubuntu-base ubuntu-desktop

c) sudo apt-get dist-upgrade

That should reinstall whatever was deleted.

---

### Post by Ben Sprinkle on 2006-05-30
i had same problem do what def said

---

