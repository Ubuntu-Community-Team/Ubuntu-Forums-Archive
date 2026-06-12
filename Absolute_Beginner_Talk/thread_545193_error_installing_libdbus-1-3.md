---
title: "error installing libdbus-1-3"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-09-07
i found a post that says  "I may have to create symbolic link in /usr/lib/
ln -s libdbus-1.so.3.0.0 libdbus-1.so.2" How would I do this?

---

### Post by Hospadar on 2007-09-07
If that's what needs to be done,
you would want to open a terminal, and type ```
cd /usr/lib
sudo ln -s libdbus-1.so.3.0.0 libdbus-1.so.2
```

But I should think that this sort of thing would have to happen after a good installation of a library.

If you don't know, a sybolic link is like a shortcut, if a program tries to use your link, it will be redirected to the link's target.  These are sometimes necesary because some programs reference different filenames for dynamic libraries like this.

---

