---
title: "Synaptic problem"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by jagannath on 2007-03-11
Would somebody help me sort this error message out ? :confused: 
" E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

Thanks,

J

---

### Post by taurus on 2007-03-11
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Najand on 2007-03-11
You are trying to install something or remove something. Can you please tell us the name of the package you were trying to install/remove, if you don't mind and can you please describe the situation when you were trying to use the apt?

---

### Post by jagannath on 2007-03-11
Thanks taurus. 
 It worked like a beaut.

J

---

### Post by jagannath on 2007-03-11
Hi Najand,
Thing is I accidentally shut down my computer while installing some updates.

J

---

### Post by Najand on 2007-03-11
That is nice you could make it.

---

### Post by jagannath on 2007-03-11
> **Najand said:**
> That is nice you could make it.

I'd be surprised otherwise. The forum staff are so helpful and so are so many others on this forum, you included.

Thanks,

J

---

