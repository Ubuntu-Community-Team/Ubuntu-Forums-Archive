---
title: "Bootchart Chart"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-09-08
What seems to be slowing the boot down?

---

### Post by DBStevens on 2007-09-09
What do you consider slow?

One thing that stands out is the readahead cache process that preloads various routines that are likely to be needed later on.

It is I/O intensive (relatively speaking) you didn't say what your hard drive system was.

---

### Post by Trzone on 2007-09-09
I'm just experimenting with Ubuntu... finally learning how to enjoy my computer with really no maintence at all. 

It's not slow per say, i am just curious as if there was anything i could have done to take off say 20 or so seconds.

I enjoy ubuntu completely =)

---

### Post by DBStevens on 2007-09-09
Other than what I pointed out which may be mitigated by improved hard drive handling (benefits elsewhere as well), removing entries that may in fact not be called upon later, or turning the read ahead caching off and letting the loads take place when needed (deferring the time cost), you'll have nitpick things more than a little.

---

