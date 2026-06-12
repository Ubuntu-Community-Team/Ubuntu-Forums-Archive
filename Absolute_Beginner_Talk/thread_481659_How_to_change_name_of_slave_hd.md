---
title: "How to change name of slave hd"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by guddr on 2007-06-22
How do I change the name of a slave HD?

---

### Post by bodhi.zazen on 2007-06-22
File system ?

Change the Label ?

Change the mount point ?

What ?

---

### Post by guddr on 2007-06-22
Change the label.  Sorry.. :(

---

### Post by Inxsible on 2007-06-22
Like so
[COLOR="Red"]Caution: mke2fs will format your drive so I would suggest you use e2label[/COLOR]
```
mke2fs -L <label> <dev>
```

```
e2label <dev> <label>
```

```
tune2fs -L <label> <dev>
```

---

### Post by guddr on 2007-06-22
Thank you.

---

