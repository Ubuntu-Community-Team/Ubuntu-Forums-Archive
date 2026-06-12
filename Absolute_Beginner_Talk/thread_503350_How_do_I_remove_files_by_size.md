---
title: "How do I remove files by size?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-07-17
How do I remove files by size?

Say I want to remove all files that are 3KB.  How would I do it?

---

### Post by yabbadabbadont on 2007-07-17
Remove files from directories in and below /example/file/path that are exactly 3k in size:
```
find /example/file/path -type f -size 3k -exec rm -f {} \;
```
Remove files from directories in and below /example/file/path that are less than 3k in size:
```
find /example/file/path -type f -size -3k -exec rm -f {} \;
```
Remove files from directories in and below /example/file/path that are greater than 3k in size:
```
find /example/file/path -type f -size +3k -exec rm -f {} \;
```

---

