---
title: "[SOLVED] Symbolic links"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by ShiningWolf on 2008-01-12
How do I create a symbolic link from one directory to another?

---

### Post by Dr Small on 2008-01-12
Like this:
```
ln -s /path/from/directory/ /path/to/linked/directory/
```

---

### Post by ShiningWolf on 2008-01-12
Thanks, but I think it is the otherway around.

Seond question: How do I remove a symbolic  link?

---

### Post by logos34 on 2008-01-12
> **ShiningWolf said:**
> Thanks, but I think it is the otherway around.

Seond question: How do I remove a symbolic  link?

there are several ways to do it.

> man ln

2.  delete the link.  (since it's not a hard link it won't delete the target)

---

