---
title: "Ooops"
date: 2005-06-17
forum: Absolute Beginner Talk
---

### Post by mr_mop on 2005-06-17
I dist-upgraded to breezy, and now have no X.
I try installing x-window-system, but there is a circular dependancy on libx6 and xlibs or something like that. :(

Is there a way to do dist-downgrade?

Thanks

MM

---

### Post by imightbegiant on 2005-06-17
I don't think there's a "dist-downgrade" option (someone correct me if I'm wrong), but after you change your repositories back to the hoary ones and updating you should be able to get everything working again by removing then installing the ubuntu-desktop package.

---

### Post by poofyhairguy on 2005-06-17
[QUOTE=mr_mop]
Is there a way to do dist-downgrade?
[/QUOTE]

Not cleanly. Time for a reinstall.

And let this be a note to other beginners:

Breezy should be considered to be off limits!

---

### Post by Xian on 2005-06-17
It would probably be possible to get a Hoary system back from your current state, but I don't think you'll see Breezy again without a reinstall.

---

### Post by mr_mop on 2005-06-19
Thanks for the help guys.  I did just that and reinstalled hoary.
Worked a treat. except for getting / and /home backwards :)
I now have my old / and my new /home on the same partion and the old /home and the new / on the other. Saved me losing any data I guess :)

---

