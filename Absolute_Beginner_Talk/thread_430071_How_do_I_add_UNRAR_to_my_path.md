---
title: "How do I add UNRAR to my path"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-05-01
I downloaded a .rar archive, and I tried to open it with Ark, but it said that unrar wasn't installed and that I needed to add it to my path.  I installed "unrar-free" in Adept, what else do I need to do?

---

### Post by Bachstelze on 2007-05-01
Try this :

```
cd /usr/bin
sudo ln -s unrar-free unrar
```

---

### Post by SuperCool4678 on 2007-05-01
That seems to have worked.
.

---

### Post by Jucato on 2007-05-01
That will only work up to a certain point and shouldn't be the correct way to do it. You will have to install the package **unrar** (not unrar-free).

---

### Post by Bachstelze on 2007-05-01
*unrar* is non-free. What if he wants to install free software only ?

---

### Post by Jucato on 2007-05-02
True that it's non-free, but only in the "freedom" sense of the term (it's monetarily free). However, the  unrar-free version does have certain limitations.

[http://packages.ubuntu.com/feisty/utils/unrar-free](http://packages.ubuntu.com/feisty/utils/unrar-free)

> Unrar can extract files from .rar archives. Can't handle archives in the RAR 3.0 format, only the non-free "unrar" package can do that.

Of course if the unrar-free works for him, then by all means stick to it.

---

