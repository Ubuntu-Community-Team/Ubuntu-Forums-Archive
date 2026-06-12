---
title: "terminal rm not working"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-07
Hi,

I made a directory and want to delete it.

```
XYZ@ubuntu:/$ sudo rm storage
rm: cannot remove `storage': Is a directory
```

I am trying to do this in the terminal but as you can see, no luck.

The location is /storage.

Thanks.

---

### Post by Klaidas on 2006-06-07
```
rm -r /path/to/that/directory
```
:)

---

### Post by Kilz on 2006-06-07
I believe another command is rmdir so it would be 
sudo rmdir /path/to/folder

---

### Post by Klaidas on 2006-06-07
rmdir works if the directory is empty
rm -r works both ways: if it's empty and if it's not ;)

---

### Post by u.b.u.n.t.u on 2006-06-07
Thank you. rmdir worked nicely.

---

### Post by Iowan on 2006-06-07
[QUOTE=Klaidas]rmdir works if the directory is empty
rm -r works both ways: if it's empty and if it's not ;)[/QUOTE]
S'pose it depends on whether you want it gone at any cost, or if you'd like a warning if it's not empty...

---

