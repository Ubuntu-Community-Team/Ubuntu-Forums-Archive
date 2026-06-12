---
title: "loading modules -&gt; Long boot"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-01-28
hi

i was trying to solve my no virtual terminal issue when i found loading 2 modules fixed it.
```
 vga16gb , fbcon 
```

however, now when i boot i get a long 1-2minutre black screen with no disk activity, then it logs me in.

i tried to remove the modules but it says they are not loaded.

anyway i can find whats hanging boot?

---

### Post by nol1ght on 2008-02-04
Do you look at your services?
System->Administration->Services

may be he try to load them but fail...

---

