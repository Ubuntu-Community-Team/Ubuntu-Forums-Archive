---
title: "How do I remove files in a sequence?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-06-14
```
rm file[08-12].foo
```
does not work.

I have read the manual, and it says nothing about how to remove files in a sequence.  `rm file*.foo` and `rm file??.foo` works, but not `rm file[08-12].foo`  Would someone please tell me how do I remove files in sequence?

---

### Post by starcraft.man on 2007-06-14
Ok, I see the problem... the way you used the set doesn't work. [Read this tutorial on linux command ]("http://www.linuxcommand.org/lts0050.php")about wildcards (pay attention to examples) and the rm/cp command. You'll see the problem and then know how to use it better, its a great site for learning the Terminal :).

---

