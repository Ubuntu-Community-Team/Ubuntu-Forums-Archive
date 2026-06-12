---
title: "Finding the version of Xorg and XFree86?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by DonQuixote on 2007-01-17
Hey all,

What is the console command to discover the version of Xorg and/or XFree86?

This curious mind wants to know. :mrgreen:

---

### Post by taurus on 2007-01-17
```
X -version
```

---

### Post by DonQuixote on 2007-01-18
Thanks!

---

### Post by dwblas on 2007-01-18
When you want to know something, try finding a man page.  Most packages have a man page.  'man program-name' will usually do it and they are very helpful.  If you have to search, they are located in /usr/share/man/man1->man9.  In this case, it is 'man xorg', which gives all of the options.

---

