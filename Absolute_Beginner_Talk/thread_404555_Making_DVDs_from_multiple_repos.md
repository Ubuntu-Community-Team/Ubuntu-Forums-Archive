---
title: "Making DVDs from multiple repos"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by trent dillman on 2007-04-08
...

---

### Post by LaurelLynn on 2007-04-08
Dear trent,

Repositories have a directory structure that includes a base folder (with whatever name you like) and then a binary and source subdirectories.  They are added to the apt-get /etc/apt/sources.list file by their URL:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted


There is nothing preventing you from installing four or more separate repositories on one DVD ( provided they fit).  You just give each a unique base folder name. Then in the sources.list file you add something like:

deb file:///media/cdrom/repistory1 binary/
deb-src file:///media/cdrom/repistory1 source/
deb file:///media/cdrom/repistory2 binary/
deb-src file:///media/cdrom/repistory2 source/
.
.

Laurel Lynn

---

### Post by trent dillman on 2007-04-08
...

---

