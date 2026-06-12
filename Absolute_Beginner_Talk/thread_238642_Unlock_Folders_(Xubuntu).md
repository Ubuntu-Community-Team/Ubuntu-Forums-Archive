---
title: "Unlock Folders (Xubuntu)"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by WPAStrangla on 2006-08-18
Former Ubuntu user I thought id give Xubuntu a try. I been trying to Unlock some folders, I type:

Alt + F2
```

gksudo nautilus
```

A window pops up and nothing happends. What am I basically doing wrong here?

---

### Post by croak77 on 2006-08-18
Is nautilus installed? I'm not sure if it's in the default Xubuntu desktop.

---

### Post by Arisna on 2006-08-18
In Xubuntu, the file manager is thunar rather than nautilus.  Please use caution when running a graphical file-manager with root privileges, especially one like thunar which does not use a Wastebasket and only uses a permanent delete operation.

That said, you should be able to change permissions on folders using a graphical file manager in Xubuntu simply by replacing "nautilus" with "thunar" in that command.

---

### Post by WPAStrangla on 2006-08-18
Thanks I got it working now :D

---

