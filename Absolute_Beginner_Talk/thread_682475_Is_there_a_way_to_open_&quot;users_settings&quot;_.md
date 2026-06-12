---
title: "Is there a way to open &quot;users settings&quot; from the command line?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-01-30
Thanks.

answer was:
sudo users-admin

---

### Post by Infinity-al on 2008-01-30
> **joesmith1234 said:**
> Thanks.
```
gksu users-admin
```

---

### Post by jan quark on 2008-01-30
if you mean the terminal by the command line 
try this
```
gksu users-admin
```

it works also in the command line just tested :)

---

### Post by joesmith1234 on 2008-01-30
> **Infinity-al said:**
> ```
gksu users-admin
```

Thanks a bunch.

I'm on ssh so I had to use normal sudo

---

