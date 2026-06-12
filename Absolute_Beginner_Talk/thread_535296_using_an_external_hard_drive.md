---
title: "using an external hard drive"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by tobyfountain on 2007-08-26
hi, whenever i try to put my movies on to my external hard drive, it tells me I cannot as I dont have the correct permissions.

How can I change this?

I have tried going to the properties of the HD, but it wont let me do anything as it says I'm not the owner.

Thanks.

---

### Post by Majorix on 2007-08-26
```
gksu nautilus
```

and then try to change the permissions again. As the root you should be able to do anything.

---

### Post by tobyfountain on 2007-08-26
that doesnt work.
it was formatted with vista.
does that help at all?

---

### Post by Steve1961 on 2007-08-26
> **tobyfountain said:**
> that doesnt work.
it was formatted with vista.
does that help at all?

In that case you probably have an ntfs partition.  If so you need the ntfs-3g driver - just search these forums for how tos e.g:

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy)

---

