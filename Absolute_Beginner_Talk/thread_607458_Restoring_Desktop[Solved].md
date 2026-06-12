---
title: "Restoring Desktop[Solved]"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by sbrody88 on 2007-11-08
Hey,
I accidentally deleted my Desktop directory, so now my home folder is being used as the Desktop...but I don't want that - I'd really like to get my Desktop back to the way it was. Anyone have any ideas how to do this? I tried simply creating a directory in my home folder named Desktop, but that wasn't enough - its just a directory named Desktop, my Desktop still shows icons from my home directory, not from the Desktop directory. Any help would be greatly appreciated!

---

### Post by Sef on 2007-11-08
If you can get to a terminal then type this command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by strabes on 2007-11-09
Make that ```
sudo apt-get install ubuntu-desktop
```

---

### Post by zero-9376 on 2007-11-09
i would try running (alt-f2) gconf-editor

browse to / > apps > nautilus > preferences

make sure desktop_is_home_dir is not ticked

The previous solution may also work but I have personally removed many packages which are dependencies of the ubuntu-desktop metapackage and reinstalling it would therefore reinstall all those applications

---

### Post by sbrody88 on 2007-11-09
I checked gconf-editor, and the desktop_is_home_dir is not ticked.  I even tried checking it, restarting, unchecking it, and restarting again.  No use.  Also, I tried reinstalling ubuntu-desktop, that didn't help either.  Does anyone have any other ideas about this?  I've been trying to figure this out for days now, to no avail...

---

### Post by sbrody88 on 2007-11-09
I just fixed it.  In ~/.config there is a file called user-dirs.dirs    I changed the line that said XDG_DESKTOP_DIR="$HOME"   to say     XDG_DESKTOP_DIR="$HOME/Desktop"  and that fixed all my problems.  Thanks to everyone who helped out!

---

