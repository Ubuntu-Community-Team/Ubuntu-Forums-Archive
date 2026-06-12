---
title: "Safe To Delete?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-04
In my home directory, i have folders called:
 .w3m, .kde and .pype
are these safe to delete? (assuming i dont want to use kubuntu desktop environment at all, and go strictly gnome?)

---

### Post by Pumalite on 2007-11-04
Better to remove totally through Synaptic. (KDE)

---

### Post by mali2297 on 2007-11-04
Removing files in your home directory won't mess up your system, they only contain your personal settings. You might want to move them to a backup though:
```

mkdir backup
mv .w3m .kde .pype backup

```
If everything works alright, you can remove the backup folder later.

---

### Post by mlentink on 2007-11-04
> **Pumalite said:**
> Better to remove totally through Synaptic. (KDE)

+1
the hidden directories in your home folder very often contain configuration info for apps currently installed. Remove those through Synaptic first and only after that delete any left-over folder.

---

