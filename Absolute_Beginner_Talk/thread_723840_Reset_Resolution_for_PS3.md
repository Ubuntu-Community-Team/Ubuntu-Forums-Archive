---
title: "Reset Resolution for PS3"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by getsome831 on 2008-03-13
I mistakenly set my PS3 resolution to something that won't display using [this guide]("http://psubuntu.com/forum/viewtopic.php?t=1262&start=15&postdays=0&postorder=asc&highlight="), but now i've sent my resolution to an incorrect setting and all i see if horizontal scrolling bars (essentially un-viewable...only shapes can be made out...no way text can).  Anybody know how i can get back into the /etc/event.d/ps3videomode file (startup script/file) to modify it without having to log into gnome...in fact, anything beyond the kboot prompt and i'm hosed.  Thanks.

---

### Post by getsome831 on 2008-03-17
I tried booting with LiveCD in hopes i could access the PS3 drive's /etc/event.d/ps3videomode file and get in to modify the upstart script that way...i can't seem to access the file system though.  Is there something i should mount, or anything else i could try?  Any thoughts?

---

### Post by Atomic Dog on 2008-03-17
If you can log in (even though the vid is all messed up), can't you hit ctrl + alt + F1 key and get into a terminal session?  From there you can edit what you need with nano.  I have a fair hunch it should work.

From that full screen terminal session you can then do a shutdown -r after you have made changes and hopefully be back in action.

---

### Post by getsome831 on 2008-03-17
Thanks Atomic Dog, i wasn't familiar enough with the Linux keyboard shortcuts to go it blind (its literally that bad).  I will give this a try though, can't hurt.

---

### Post by getsome831 on 2008-03-18
I tried with nano but could not make out enough to edit the script.  In fact, i couldn't even tell if nano opened up the file after i ran sudo nano filename +password.  There has to be another way i can get to that file!  Any thoughts?

---

### Post by getsome831 on 2008-03-19
Well, i was finally able to get in and edit it.  Through a combination of "Alt + F2" (run application shortcut - sudo gedit /etc/event.d/ps3videomode +password when prompted) and the freeze function on my sony tv (kind of like taking a screenshot and displaying it).  Everything is back to normal now.

---

