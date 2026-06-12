---
title: "Install OS X after installing Ubuntu?"
date: 2008-12-15
forum: Apple Hardware Users
---

### Post by hyperboloid on 2008-12-15
Here is maybe a dumb question. I have a working, well tuned Ubuntu 8.10 installation on my MBP, but when I did the original install I wiped out OS X. I don't like OS X very much, and am much happier now, but I have read that maybe it is a good idea to keep a small OS X installation for firmware updates. 

So, is it possible to reinstall OS X without losing my current Ubuntu? In effect, I'd like to create a dual boot setup starting from Ubuntu and adding OS X. I don't currently have rEFIt installed, and I'd like to keep the default to boot into Ubuntu.

Anybody out there who has already done this? Please advise the best strategy for this, if indeed it is possible at all. My current partition table looks like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1          16+  ee  GPT
/dev/sda2   *           1       23330   187396484+  83  Linux
/dev/sda3           23330       24322     7964466   82  Linux swap / Solaris

```

---

### Post by cyberdork33 on 2008-12-15
Well, since it appears you did not convert the disc to a normal MBR format, you can use gparted to shrink your Linux partition and then Boot the OSX dvd, use diskutility to add an OSX partition and install.

---

