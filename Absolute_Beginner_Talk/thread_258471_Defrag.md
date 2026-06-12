---
title: "Defrag"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Christopher Cook on 2006-09-16
On windows there were things to defrag, clean, free up space, etc. Are there ways to do this on Ubuntu?

---

### Post by tagra123 on 2006-09-16
I'm sure someone will give a more technical answer than min but there is no need to defrag.

From my understanding ext3 automatically keeps itself defraged.

---

### Post by wieman01 on 2006-09-16
You don't need defrag on Linux, the file system is much more advanced than Windows'.

As for the other questions... Here is a useful link:

[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

Plus you can always free up space by removing cached Debian files in "/var/cache/apt/archives", just DON'T delete the "partial" folder in there.  It's safe to remove the *.deb files.

---

