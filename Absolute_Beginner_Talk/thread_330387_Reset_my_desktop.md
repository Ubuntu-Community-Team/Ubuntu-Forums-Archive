---
title: "Reset my desktop"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by URR on 2007-01-03
I would like to know how I can reset my desktop menus, panels and things...

Seemed to have deleted things and moved them around by mistake, and can't get it back to the way it was???

Thank you!

Loving Linux!

---

### Post by viciouslime on 2007-01-03
If you delete the .gnome2 folder in your home directory, everything you mention should be reset. The folder is hidden, so if you want to delete it through nautilus, press ctrl+h to see it.

One idea might be just to rename it for now, in case there is a setting in there you actually want to keep. If you rename it to .oldgnome2 then log out and then back in, check everything is ok and then you can delete it. Else, delete the newly created .gnome2 and rename .oldgnome2 back to .gnome2 this will restore everything to the way it is now.

I'll keep watching this thread in case you have problems :)

---

