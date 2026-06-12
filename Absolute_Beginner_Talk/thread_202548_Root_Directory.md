---
title: "Root Directory"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-06-23
I just installed GAP using the following command:

```
sudo aptitude install gap
```
and the installation seemed to have been successful.  However, I need to find the root directory to install an additional package but I cannot do so.  I have tried a search and have looked though the folders myself but cannot find anything that has to do with "gap."  Does anyone know where this might be?

Thanks.

---

### Post by aysiu on 2006-06-23
Try this: ```
sudo updatedb
locate gap
```

---

### Post by echo $USER on 2006-06-23
/root

---

