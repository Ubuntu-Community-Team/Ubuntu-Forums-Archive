---
title: "Xorg.conf Configuration"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Darkblizz on 2007-10-06
K so i want to change my mouse settings went to do it and it says that i can't save it because the file is read only! Do i need to log in as root to do this and if i do how do i log in as root considering when i try to from the login screen says i cannot do it here!?

---

### Post by finer recliner on 2007-10-06
gksudo gedit /etc/X11/xorg.conf

---

### Post by por100pre1 on 2007-10-06
> **finer recliner said:**
> gksudo gedit /etc/X11/xorg.conf

Backup your xorg.conf file first!

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

