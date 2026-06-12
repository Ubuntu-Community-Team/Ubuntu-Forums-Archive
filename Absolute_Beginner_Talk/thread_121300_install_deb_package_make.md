---
title: "install deb package make"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by newbee on 2006-01-24
My kdevelop complains there is not "make"...
How do I install the debian make package if I download the make package from [http://packages.ubuntu.com/breezy/devel/](http://packages.ubuntu.com/breezy/devel/)  ?

The computer does not have a net connection.

---

### Post by Adrian on 2006-01-24
[QUOTE=newbee]My kdevelop complains there is not "make"...
How do I install the debian make package if I download the make package from [http://packages.ubuntu.com/breezy/devel/](http://packages.ubuntu.com/breezy/devel/)  ?

The computer does not have a net connection.[/QUOTE]

Try:
```
dpkg -i <packagename>
```
where <packagename> is your .deb file (make).

---

