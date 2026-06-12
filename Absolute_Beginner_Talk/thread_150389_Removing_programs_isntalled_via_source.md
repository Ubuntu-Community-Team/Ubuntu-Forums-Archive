---
title: "Removing programs isntalled via source?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by rj686 on 2006-03-25
How do you take out a program you installed through source, i just realized i installed azureus in German.

---

### Post by 3rdalbum on 2006-03-25
I've never removed from source, but I believe you navigate into the source directory and type "make remove". (assuming it uses the normal system for compiling). Otherwise, the Makefile should tell you where all the program's files are, so you can remove them.

---

### Post by taurus on 2006-03-26
From where you built the program, run
```

sudo make uninstall

```

---

### Post by nickj6282 on 2006-03-26
Another alternative that I like is to use checkinstall. You can install it from apt (apt-get install checkinstall). Then, when you're compiling/installing from source you do this instead:

```

./configure
make
sudo checkinstall -D

```

This will create a Debian package (.deb) and install it for you. Then, when you want to uninstall later, you can just do a **dpkg -remove name-of-package**.

---

### Post by tr333 on 2006-04-07
[QUOTE=nickj6282]Another alternative that I like is to use checkinstall. You can install it from apt (apt-get install checkinstall). Then, when you're compiling/installing from source you do this instead:

```

./configure
make
sudo checkinstall -D

```

This will create a Debian package (.deb) and install it for you. Then, when you want to uninstall later, you can just do a **dpkg -remove name-of-package**.[/QUOTE]
thanks for the info on this.

---

