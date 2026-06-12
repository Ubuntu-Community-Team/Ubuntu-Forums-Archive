---
title: "A problem with bad xorg.conf?"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2006-03-03
I obviosly wrote wrong parameters in the xorg.conf file. As a result the gnome desktop doesn't start. How do I load the backup file, which is in the same /etc/X11/?

---

### Post by dwessell on 2006-03-03
If you have access to the shell, or terminal..

```


cd /etc/X11

sudo rm xorg.conf

cp backupnamehere xorg.conf


```

---

### Post by Zdravko on 2006-03-03
dwessell, ok, but how do I "dir" all files in that directory? Including with atribute like "date of last editing"?

---

### Post by Klaidas on 2006-03-03
DO you mean list all the files in a directory? If so, ```
ls -l
```

---

### Post by Zdravko on 2006-03-03
Again, thank you for the information. It appears that after a "dpkg-reconfigure xserver-xorg" it wasn't possible to directly load the new parameters. After a reboot, everything is fine.

---

### Post by Klaidas on 2006-03-03
Nice to see it's working for you ;)

---

