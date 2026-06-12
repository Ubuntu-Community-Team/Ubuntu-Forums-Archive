---
title: "gedit: cannot open shared object file"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by caravel on 2006-10-19
On trying to run gedit this evening I get this error message:

```
gedit: error while loading shared libraries: libpython2.4.so.1.0: cannot open shared object file: No such file or directory
```

I've googled it but can't find anything anywhere.  It occurs when running sudo gedit or just gedit. Everything was fine yesterday and now when I booted up today this.  ](*,)

---

### Post by gborzi on 2006-10-19
Have you checked if /usr/lib/libpython2.4.so.1.0 is still in place ? If it is not, or you suspect it's corrupt (check with *debsums python2.4*), try to reinstall the python2.4 package, i.e.
> sudo apt-get install --reinstall python2.4

---

### Post by caravel on 2006-10-19
That worked!  Thanks. :mrgreen:

It was there but it must have got itself corrupted... :-?

---

