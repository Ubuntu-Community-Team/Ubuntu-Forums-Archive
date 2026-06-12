---
title: "no right click on desktop...."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by sp0onman on 2007-09-13
ok so i installed the athlon k7 kernel([http://ubuntuforums.org/showthread.php?t=85917&highlight=kernal](http://ubuntuforums.org/showthread.php?t=85917&highlight=kernal)) 

and after i restarted i get a black wallpaper and cant right click on the desktop, everything else works just fine. has anybody else ever had this problem or is there anyone out there that can let me know how to fix this?

---

### Post by audax321 on 2007-09-13
Try this:

1.  Applications > System Tools > Configuration Editor

2.  Go to apps > nautilus > preferences

3.  On the right half of the window make sure 'show_desktop' is checked (true)

For the wallpaper:

1. Applications > System Tools > Configuration Editor

2. Go to desktop > gnome > background

3. Make sure the 'draw_background' option is checked (true)

4. If the 'picture_filename' option in that same section is blank (or invalid if you deleted the wallpaper or something), you'll have to go set a wallpaper image as background as you usually would, otherwise the wallpaper should show up on your desktop after checking 'draw_background'

If that works, somehow those options got unchecked and I have no idea why LOL... a kernel update shouldn't have done that. If it didn't work then I have no clue, good luck! :)

---

### Post by sp0onman on 2007-09-13
yea checked all that its none of that. my wallpaper wasn't deleted. i can still make it my wallpaper if i open the file. thanks for trying, anyone else have any idea's?

---

### Post by sp0onman on 2007-09-16
it 'fixed' itself for a couple days now its happening again, i dont know why, somebody help pls? btw im using the 8.40 flgrx drivers on a x800pro( if it has somethin to do with it) and compiz-fusion with xgl. when i login without xgl or compiz running the same thing is happening.

---

### Post by sp0onman on 2007-09-16
bump

---

### Post by Tyke91 on 2007-09-16
is it no right click, or no desktop.

can you still put icons on your desktop? if not, run this command

```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true && nautilus
```

---

