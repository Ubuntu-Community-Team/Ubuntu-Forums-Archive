---
title: "linix-source?"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by cvogel on 2005-06-16
Hello. I'm fairly new to linux and am trying to install the latest madwifi module. Apparently, the one that comes with ubuntu is too old. I was told in an earlier forum to download linux-tree with synaptic, which places a .bz2 file in my /usr/src directory.  This may sound novice, but I am, so what I wanted to know is this: Should I do anything special with it before extracting.. or should I just extract it and be happy?

Thanks

---

### Post by Xian on 2005-06-16
Extract that linux-source-2.6.10.tar.bz2 file in the /usr/src directory.
That should leave you with these contents:

```
$ ls /usr/src
linux-patches  linux-source-2.6.10  linux-source-2.6.10.tar.bz2  rpm
```
Then you will want to make a symlink to the kernel source folder.
Input this into a teminal:

```
$ cd /usr/src
$ sudo ln -s linux-source-2.6.10 linux
```

Now you will see that we can access that folder with the symlink:
```
$ ls /usr/src/linux
arch     Debian.src.changelog  include  lib          net             scripts
COPYING  Documentation         init     MAINTAINERS  README          security
CREDITS  drivers               ipc      Makefile     README.Debian   sound
crypto   fs                    kernel   mm           REPORTING-BUGS  usr
```

---

### Post by cvogel on 2005-06-16
thanks a lot :) just saw my typo: "linix.") haha linux.. sorry

---

