---
title: "[SOLVED] error: Did not find GTK+ installed (even tho I got it)"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by gorgon on 2008-03-06
Hi,

I'm trying to build a program but when I do ./configure i get:
checking for GTK 1.x... configure: error: Did not find GTK+ installed

But I got libgtk2.0-dev installed and doing a 'locate gtk+' gives me:
/usr/lib/pkgconfig/gtk+-unix-print-2.0.pc
/usr/lib/pkgconfig/gtk+-x11-2.0.pc
/usr/lib/pkgconfig/gtk+-2.0.pc

Am I just being plain silly or just really noobious, or both :) ?

---

### Post by kellemes on 2008-03-06
What program are you trying to compile?
It seems to ask for gtk 1.x ??
Not sure if this is what you want since it's old and generally not needed for up to date gtk-packages.

---

### Post by gorgon on 2008-03-06
Yes, you're right:
[http://sourceforge.net/project/showfiles.php?group_id=94277&package_id=118299](http://sourceforge.net/project/showfiles.php?group_id=94277&package_id=118299)

The program hasn't been updated since 2004.. So, would I have to get an old gtk version? Would that mess with anything else?

Seems strange it's not backwards compatible..

---

### Post by kellemes on 2008-03-06
Ok, I don't know anyting about the software you're trying to install, but that's not important.
If it wants GTK 1, it can have it..
You can install GTK 1, including the development-package since you're going to build, like so..
from terminal..
```

sudo apt-get install libgtk1.2-dev

```
It will install a couple of packages and I can't imagine it will mess-up anything.

---

### Post by gorgon on 2008-03-06
thanks, I'll try it out!

---

