---
title: "yaboot error"
date: 2009-03-23
forum: Apple Hardware Users
---

### Post by paul_mcl on 2009-03-23
Just built a new kernel ( 2.6.29-rc8 ) via make-kpkg, installed it via dpkg -i, rebooted and got this error on yaboot:

```
ext2: i/o error 2133571364 in read
Read failed
```

vmlinux' ELF seems to be perfect (readelf has no problem with it)
fscked disk: it is okay
Maybe some kind of kernel's size limitation in yaboot?

Any help on this issue would be great.

---

### Post by paul_mcl on 2009-03-24
Compiled fresh git master branch (v2.6.29)...
Same **** - same error.

---

