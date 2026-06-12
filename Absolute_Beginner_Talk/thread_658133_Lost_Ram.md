---
title: "Lost Ram"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-04
Right before opening firefox, system monitor told me that I am using 42 % (215MB) of RAM. However, when I check my processes, the top few (in memory usage) read like this:

XGL   -    66.4
Nautilus - 13.4
checkgmail - 9.5
gnome panel-9.5
python - 8.3
emerald - 5.0

Where has the rest of my RAM gone?

---

### Post by hyper_ch on 2008-01-04
```

free -m

```

What does that return?

---

### Post by intense.ego on 2008-01-04
I got this

```
             total       used       free     shared    buffers     cached
Mem:           502        494          8          0         25        190
-/+ buffers/cache:        277        225
Swap:         1160        220        940

```

---

### Post by hyper_ch on 2008-01-04
well, you're using the ram...

---

### Post by intense.ego on 2008-01-04
But where is it being used up?

---

### Post by hyper_ch on 2008-01-05
half of it is cache

---

### Post by intense.ego on 2008-01-05
Could I just delete the cached memory or will that just make things run slower?

---

### Post by davidsrsb on 2008-01-05
cache ram is made available for applications as soon as it is needed. Why waste ram by keeping it empty

---

### Post by philinux on 2008-01-05
This behaviour is quite normal.

---

### Post by intense.ego on 2008-01-05
so, except for upgrading my RAM (which I plan on doing soon), there isn't anything I can do?

---

### Post by SOULRiDER on 2008-01-05
Cache is good, the more RAM youre using things will most ptobably run faster. Remember, thsi si not windows' horrible memory management ;)

---

### Post by Miademora on 2008-01-05
Only worry if your system is using a lot of swap. Until then youre totally fine.

---

### Post by intense.ego on 2008-01-05
And how much swap would be a lot? According to system monitor I am using 351.3mb out of 1.1 gb (30.3%).

---

### Post by SOULRiDER on 2008-01-05
Thats fine because you dont ahve that much RAM. Dont worry about it.

---

