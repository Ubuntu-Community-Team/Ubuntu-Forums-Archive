---
title: "apt-file, apt-cache, and findpkg commands in ubuntu?"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by johnnymo87 on 2006-01-13
I'm looking to install e17 as a window manager per SFN's instructions in his HOWTO post [[http://ubuntuforums.org/showthread.php?t=61488]](http://ubuntuforums.org/showthread.php?t=61488]).

The first thing I need to do is download some debian packages.

libc6
libc6-dev
libc6-i686
locales
libvorbis0a
libextractor1

Unfortunately, the site he recommends to download them from (packages.debian.org) is down at the moment.

But the site says I can search for these files on Google:
> You can use apt-file, apt-cache search and findpkg (--> Google) as a temporary replacement.

I tried playing with the findpkg command. Doesn't exist. How do I use these commands in ubuntu?

---

### Post by aysiu on 2006-01-13
How about [http://packages.ubuntu.com](http://packages.ubuntu.com) ?

---

### Post by timfrost on 2006-01-13
apt-cache is part of the default install.

```

tim@marvin:~$ apt-cache search libc6-dev
libc6-dev - GNU C Library: Development Libraries and Header Files
libc6-dev-amd64 - GNU C Library: 64bit Development Libraries for amd64
libc5-altdbg - The Linux C library version 5 (alternative debug files).
libc5-altdev - The Linux C library version 5 (alternative dev files).
libdl1-altdev - The Linux dynamic linker library (libc5 altdev files).

```

apt-file is in the universe repository.  See [https://wiki.ubuntu.com/Repositories](https://wiki.ubuntu.com/Repositories)

---

### Post by johnnymo87 on 2006-01-13
thanks. :)

---

