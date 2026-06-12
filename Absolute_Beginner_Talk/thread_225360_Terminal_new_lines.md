---
title: "Terminal new lines"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Touch.Code on 2006-07-29
I am trying to get a command line but I need to know how to start a new line without pressing enter!

---

### Post by aysiu on 2006-07-29
I'm sorry--can you explain a bit more what your problem is... maybe with a screenshot?

---

### Post by Touch.Code on 2006-07-29
OK, lets say I want to type this is:

```
$ sudo
$ sudo
```

But, I cant press enter, I need to start a new line before I press enter!

---

### Post by aysiu on 2006-07-29
So you want to combine two commands? Use *&&* then.

For example, if you wanted to combine ```
sudo aptitude update
``` and ```
sudo aptitude install acroread
``` you would combine them this way and have to press **Enter** only once ```
sudo aptitude update && sudo aptitude install acroread
```

---

### Post by Touch.Code on 2006-07-29
Thankyou very much XD!

---

