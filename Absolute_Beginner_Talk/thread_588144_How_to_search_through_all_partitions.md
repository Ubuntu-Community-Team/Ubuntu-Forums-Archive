---
title: "How to search through all partitions"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by netimen on 2007-10-23
The tracker search searches only files wich are on the same partition with the start folder. How to make it search through all partitions?

---

### Post by plinydogg on 2007-11-01
I'd like to know how to do this too!

---

### Post by taurus on 2007-11-01
Applications -> Accessories -> Terminal
```
sudo find / -name **filename** -print
```
Replace filename with the file that you want to search.

---

### Post by plinydogg on 2007-11-01
Thanks Taurus! After I posted I also found the method described here:

[http://ubuntuforums.org/showthread.php?t=370703](http://ubuntuforums.org/showthread.php?t=370703)

Does one method have a particular advantage over the other?

Thanks again!

---

### Post by netimen on 2007-11-02
Thanks Taurus, but I'd like to know how to configure the Deskbar applet to search through all partitions, not through just /

---

### Post by Rinzwind on 2007-11-02
> **plinydogg said:**
> Thanks Taurus! After I posted I also found the method described here:

[http://ubuntuforums.org/showthread.php?t=370703](http://ubuntuforums.org/showthread.php?t=370703)

Does one method have a particular advantage over the other?

Thanks again!

'locate' only finds files that are inside the database created with 'updatedb but locate is a heck of alot faster than find. 'find' always finds it if it's on your system (unless you search the wrong items ;) )

---

