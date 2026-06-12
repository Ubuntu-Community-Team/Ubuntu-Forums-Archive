---
title: "Getting mkdir error: no such file DOSBOX install"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by cdcweb on 2008-02-22
Trying to follow this [DOSBOX Install](https://help.ubuntu.com/community/DOSBox), and while following the tutorial, i keep getting a mkdir error when tyring to create the dos/c directory.

What am I doing wrong? Used sudo as well

mkdir ~/dos/c

---

### Post by yabbadabbadont on 2008-02-22
```
mkdir -p ~/dos/c
```

You have to use the '-p' option if you want to create a directory tree, instead of just a single directory.

---

