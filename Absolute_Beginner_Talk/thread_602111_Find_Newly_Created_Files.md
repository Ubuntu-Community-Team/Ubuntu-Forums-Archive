---
title: "Find Newly Created Files"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-11-03
How can I find files created today? I just downloaded a bunch of mp3 files into an existing directory (with sub-directories) that already contained a lot of mp3's and I want to locate and copy only the newest ones to my mp3 player. A solution using either Nautilus or the command line (whichever does the job best) works for me. Thanks.

---

### Post by haldean on 2007-11-04
```
ls -lc | grep 2007-11-04
```
Will give you a list of files modified today in a directory.

---

