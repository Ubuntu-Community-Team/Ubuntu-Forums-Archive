---
title: "What's these core.##### files in my homedir?"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by olavjunior on 2008-11-04
I've suddenly started to get multiple core.##### files in my home dir. What are they? They're pretty large as well (300-400 megs)

---

### Post by cyberdork33 on 2008-11-04
Sounds like core dumps from something crashing.

---

### Post by olavjunior on 2008-11-04
Yea, that sounds likely. How do I read them?

(I've had A LOT of kernel panics lately. But nothing gets dumped then, right?)

---

### Post by cyberdork33 on 2008-11-04
> **olavjunior said:**
> Yea, that sounds likely. How do I read them?

(I've had A LOT of kernel panics lately. But nothing gets dumped then, right?)
nope, I'd say they are kernel dumps then when you have a panic. If you can figure out what causes the panics, you can file a bug and attach the dump. That will help the developers determine the problem. Otherwise they just take up space and you can delete them.

---

