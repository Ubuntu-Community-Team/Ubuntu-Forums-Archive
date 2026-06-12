---
title: "changing ubuntu logo on menu bar."
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-10-17
I am trying to figure out how to change the default ubuntu logo on my menu bar where it says applications places system.
I read a small tutorial on where the ubuntu picture is stored and I changed it to the picture that i want displayed but nothing changed. does anyone know how to change it.

Here is the command that I used to change the logo.
> sudo cp gnome-foot.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png 

when I go into the directory I can see that the picture is changed but when I reboot the ubuntu logo is still there and the gnome foot does not appear.

---

### Post by sitedesign on 2006-10-17
Check out this thread for better cover on the subject, you can use the gconf editor to do it.

[http://www.ubuntuforums.org/showthread.php?t=156462](http://www.ubuntuforums.org/showthread.php?t=156462)

---

### Post by catlett on 2006-10-17
That may not be the correct directory. Did you check the directory before copying the gnome foot to make sure it was the correct directory? It seems highly imprbable that the ubuntu logo could appear if it was removed from the correct directory.
If you were following Laura Tamila's How TO, she cautions 
> I'm not sure is this the right directory for Dapper!
sudo cp apple.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png 
I would reboot just in case that has something to do with it and then I would search in /user/share for a directory with the ubuntu logo

---

