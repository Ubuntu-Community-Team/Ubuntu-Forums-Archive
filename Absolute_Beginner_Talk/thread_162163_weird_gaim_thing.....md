---
title: "weird gaim thing...."
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-18
I was messing around trying to get gaim themes to work ect, so I guess I clicked something wrong. But now when i go to the menu and start gaim, my buddy list comes up, but if i click x or  minimize, the window just disappears.  clicking gaim again just starts a new buddy list. i have to go to processes and kill it to see where it is.  also, gaim used to pop up when i turned on comp. but no more...any idea what i did, or can i just un/reinstall gaim?

---

### Post by Kimm on 2006-04-18
if you do:

rm -rf .gaim

in your terminal all settings should be back to the way they where when you first ran it (Linux apps cant keep settings information anywhere besides the home directory).
This however, means that you have to configure all your acounts again.

As for Gaim starting when GNOME does, check "save session" when logging out, or open "Sessions" under Settings and check "allways save session"
Just make sure Gaim is running when you logout/shut down

---

