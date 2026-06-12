---
title: "How do I copy everything?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-07-10
How do I copy everything?  Including hidden files.

```
cp -R folder location
```
does not copy the hidden files.

---

### Post by aysiu on 2006-07-10
It should copy the hidden folders. It may not preserve hard links or symlinks, though.

---

