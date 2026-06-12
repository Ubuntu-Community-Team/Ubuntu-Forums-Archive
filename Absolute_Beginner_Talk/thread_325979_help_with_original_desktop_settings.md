---
title: "help with original desktop settings"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by sn0m on 2006-12-26
hi guys, im an absolute beginer and plaed up with desktop settings, toolbars and themes.
now  system is in the mess.
Does anybody know how to restore the original desktop, toolbar and theme settings.
thanks
sn0m

---

### Post by taurus on 2006-12-26
Probably have to remove  ~/.gconf, ~/.gnome, ~/.gnome2, & ~/.gnome2_private...  So at the GUI login screen, press <Ctrl><Alt>F2 and log in to a console with your name and password.  Then, remove those hidden directories with

```
rm -rf ~/.gconf ~/.gnome ~/.gnome2 ~/.gnome2_private
```
Log out (**exit**)and press <Alt>F7 to get back to the GUI login screen and login again.  See if you get back to the default settings...

---

### Post by sn0m on 2006-12-27
wow, that sorted it out, cool beans.
ta budy
i'll be back soon with some more stupid mess up.

---

### Post by JNik on 2007-01-17
Thanks taurus

I had the same problem.

---

### Post by ghostboy on 2007-05-18
This worked out great for me also!  Thanks!!!!:)

---

