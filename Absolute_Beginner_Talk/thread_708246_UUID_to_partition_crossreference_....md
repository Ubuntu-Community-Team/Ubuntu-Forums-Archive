---
title: "UUID to partition crossreference ..."
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-02-26
Is there a command that will reveal the currently designated partition for a UUID?

Carl

---

### Post by jan quark on 2008-02-26
perhaps this

```
ls /dev/disk/by-uuid -alh
```

---

### Post by jeffus_il on 2008-02-26
You can write a little script maybe a one liner, what is the "currently designated partition" ?

---

