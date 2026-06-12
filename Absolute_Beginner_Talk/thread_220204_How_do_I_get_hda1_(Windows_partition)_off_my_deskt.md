---
title: "How do I get hda1 (Windows partition) off my desktop?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-07-21
I can get it off with the terminal, but when I reboot it's comes back. How do I stop it from appearing at all?

---

### Post by Malac on 2006-07-21
```
sudo gedit /etc/fstab
``` there should be an entry like ```
/dev/hda1       /media/C_Win98    vfat    rw,user,umask=000  0       0
``` or something similar comment this out with  a # sign.

---

### Post by crossedout on 2006-07-21
Or, you could try Applications --> System Tools --> Gnome Configuration Editor
Expand apps --> nautilus --> desktop.  Uncheck the volumes_visible option.

That should do what you are asking.

-crossedout

---

### Post by aysiu on 2006-07-21
I think the configuration editor is hidden in Dapper (unchecked in the A la Carte menu editor).

So if you don't see it in Applications > System Tools, just press Alt-F2 and type ```
gconf-editor
```

---

