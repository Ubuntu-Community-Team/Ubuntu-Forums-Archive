---
title: "Python library directory"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by homunq on 2007-08-02
OK there is obviously an easy answer to this.

I've been using Linux once-in-a-while for years - I've installed it at least 10 times, some of them tricky, at least 5 on computers I owned, at least 3 distros - I'm not a newbie. But I've never really systematically figured out what goes where, so suddenly I have a TOTAL newbie question.

I have python and idle installed. Now I want to look at the source for idle, in idle. Where do I look? If I need some other idle-source package, what is it called, and where does it dump the code once it gets it?

I'm gonna come back to this in 4 hours, if there's no answer I'll figure it out myself. A really good answer would tell me where I should have found the answer.

Thanks!

---

### Post by apswartz on 2007-08-02
I used...
```
locate idle |grep python
```
and came up with... /usr/lib/python2.5/idlelib/

---

