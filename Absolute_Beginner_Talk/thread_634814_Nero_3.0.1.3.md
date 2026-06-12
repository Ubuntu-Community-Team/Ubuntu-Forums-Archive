---
title: "Nero 3.0.1.3"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by subs on 2007-12-08
I have a copy of nero 3.0.1.3 for linux.....

i dont know how to install it..... from what i understood i have to run the *"nero"* file in */usr/bin* on the cd..... but then i get this error.....

> ./nero: error while loading shared libraries: libNeroAPI.so: cannot open shared object file: No such file or directory

i thought it was some problem with the permissions....  so i copied all the contents of the cd onto my hard disk and then i tried to chmoding all the files to 777.... ie

>  sudo chmod 777 -R *

but that doesnt seem to help...... any suggestions will be welcome!!!:):)

---

### Post by shirilover on 2007-12-08
Did you download the deb version?
If so, it's as simple as
```

sudo dpkg -i nerolinux-3.0.1.3-x86.deb

```

---

### Post by subs on 2007-12-10
i dont have a deb package for nero...... the deb package available is for v3.0.2.1 and i have a license for v3.0.1.3

---

### Post by ViRMiN on 2007-12-10
Your license will work ;)

---

