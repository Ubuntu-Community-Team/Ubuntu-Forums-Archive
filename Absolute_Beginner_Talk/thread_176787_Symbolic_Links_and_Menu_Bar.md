---
title: "Symbolic Links and Menu Bar"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by tc10b on 2006-05-15
Hi, I just wondered if it was possible to remove the symbolic link symbol on the icons, like you can do in windows. It's not a big deal just wanted to know if it's possible.

Oh and how do you change the logo on the menu bar from the ubuntu logo to say the gnome logo? I've seen a few people with different icons and I'd like to be able to change mine.


Thanks a lot


Tom

---

### Post by halfvolle melk on 2006-05-15
Hi Tom,
Not sure I understand the first question but for the second, check out these links:
[http://doc.gwos.org/index.php/Gnome_Icon](http://doc.gwos.org/index.php/Gnome_Icon)
[http://ubuntuforums.org/showthread.php?t=75034](http://ubuntuforums.org/showthread.php?t=75034)

---

### Post by tc10b on 2006-05-15
Thanks!

Do you know if I can adapt this for any picture or just the gnome icon.

---

### Post by halfvolle melk on 2006-05-15
Here's what I did:
```
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.bak

sudo cp /usr/share/icons/hicolor/48x48/apps/gnome-nibbles.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png

killall gnome-panel
```
That works, ie. copy any png to .../distributor-logo.png. Dunno if it has to be 48x48.

---

