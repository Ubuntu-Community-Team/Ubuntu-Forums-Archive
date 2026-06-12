---
title: "No Sound With Flashplayer..."
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-08-15
I've got the latest Macromedia flash extension installed, but it won't play any sound. 

The sound on everything else works great...  any ideas?

---

### Post by Jagot on 2006-08-16
Try this:

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd
```

---

