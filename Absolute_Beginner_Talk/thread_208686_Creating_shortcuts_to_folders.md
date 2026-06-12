---
title: "Creating shortcuts to folders?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by battleroyalex on 2006-07-03
I want to creat a shortcut to my documents on my windows partition onto my linux home/username/

how do I do this :oops:

---

### Post by aysiu on 2006-07-03
Are you using KDE, Gnome, or XFCE?

---

### Post by battleroyalex on 2006-07-03
Gnome, oh btw Make Link is grayed out in my windows partiton

---

### Post by professor_chaos on 2006-07-04
[QUOTE=battleroyalex]I want to creat a shortcut to my documents on my windows partition onto my linux home/username/

how do I do this :oops:[/QUOTE]

Your windows partition is probably NTFS and you aren't able to create a link via the GUI/Nautilus because that would require writing to the windows partition, and your not able to safely write to NTFS.

insead you can open up a terminal window and type```
 ln -s /mnt/windowsdrive/path2mydocuments /home/username/nameoflinktodocuments
```

this will make a shortcut/link

---

### Post by aysiu on 2006-07-04
You can also middle-click-drag the folder to your desktop and select **link here**.

---

