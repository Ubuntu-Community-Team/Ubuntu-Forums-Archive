---
title: "Ushare dependency issues"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by MrEpic on 2007-12-20
When I try to install uShare on Ubuntu 7.04, I get the following

ushare:
 Depends: libavcodec1d (>=0.cvs20070307) but it is not installable
 Depends: libavformat1d (>=0.cvs20070307) but it is not installable
 Depends: libavutil1d (>=0.cvs20070307) but it is not installable

Anyone know how to fix this?

Thanks

C.

---

### Post by zvacet on 2007-12-20
```
sudo apt-get install libavcodec1d  libavformat1d libavutil1d
```

or you can try

```
auto-apt run ./configure
```

---

