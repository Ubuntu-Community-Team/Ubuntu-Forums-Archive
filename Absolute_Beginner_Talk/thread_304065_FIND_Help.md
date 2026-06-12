---
title: "FIND Help"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by derby007 on 2006-11-21
Could someone help with the FIND command: i want to use FIND to search for files, but only on my 'filesystem' ie. / >> /var & not the mounted filesystems.... :-k

---

### Post by LLRNR on 2006-11-21
See **find --help** for more details, but when you issue find to search for things in a certain location, you can use
```
find /path/to/file thing_to_find
```
This way you'll only search files within the specified path.

HTH,

LLRNR

PS - You can also try **man find** for detailed instructions.

---

### Post by Arndt on 2006-11-21
> **derby007 said:**
> Could someone help with the FIND command: i want to use FIND to search for files, but only on my 'filesystem' ie. / >> /var & not the mounted filesystems.... :-k

Maybe

```
find -xdev
```

is what you want.

---

### Post by tocleora on 2006-11-21
This may be an old school way of doing it (I learned it in Red Hat 5) but I always do a find like this:

find [path] -name [filename] -print

or like

find . -name xorg.conf -print

I've noticed the path is required on freebsd but usually in ubuntu and fedora I just cd / and then find -name xorg.conf -print.

Better way to do it now?

---

