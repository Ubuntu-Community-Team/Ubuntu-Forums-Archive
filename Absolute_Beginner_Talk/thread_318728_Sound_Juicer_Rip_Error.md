---
title: "Sound Juicer Rip Error"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by davebed on 2006-12-14
My Sound Juicer loads automatically when I insert a CD.
When I try to EXTRACT the CD I get
"Extraction Failed: Access denied".

WHen I ```
gksudo sound-juicer
``` then everything works fine.

So it seems pretty straight forward, but how to I make sound-juicer load with root permissions?

Thanks for you help :)

---

### Post by dbd on 2006-12-14
I'm not sure how to make it automatically run with root permissions in Gnome (since I'm a KDE user, and I'm assuming your in Gnome) but it would probably be something to do with the program associated with audio CDs.

Really your shouldn't need to run it as root anyway. Does your user have write permission where you are extracting the files?

---

