---
title: "Transmission 0.80 problem"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by greedz on 2007-08-10
Hey guys, i need some help.

After i upgraded to 0.80, Transmission won't start. This is what i get:
```

greedz@maggie:~$ transmission-gtk
transmission-gtk: completion.c:130: tr_cpEnsureDoneValid: Assertion `have <= total' failed.
Aborted (core dumped)

```
Also, i found this [thread](http://transmission.m0k.org/forum/viewtopic.php?t=2131) on the official forums, it's about the MacOSX version however it seems to be the same problem, and it was solved.

Any ideea what's the.. err, ubuntu version of *~/Library/Application Support/Transmission* , and what should i delete so it would work again?

Thanks in advance!

Edit: nevermind, i just deleted the cache and it worked again.

---

