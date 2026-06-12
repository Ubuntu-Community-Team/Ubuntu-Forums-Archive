---
title: "Available update dependencies ?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by oygle on 2005-12-28
Just after installing version 5.10, I get a (big) list of available updates, the list shows 41 of them (57.1 Mb).

Is there any method to tell of update dependencies, as I don't want to download every update now, just any critical ones.

Version 5.10 was released in Oct, and already there are 41 updates, ..wow

Oygle

---

### Post by Jussi Kukkonen on 2005-12-28
What does your */etc/apt/sources.list* say?

If you only want security updates one line should be enough, something like:
```
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe
```

---

### Post by oygle on 2005-12-28
[QUOTE=Jussi Kukkonen]What does your */etc/apt/sources.list* say?

If you only want security updates one line should be enough, something like:
```
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe
```[/QUOTE]

The ../sources.list has a lot more lines than that in it. As I don't know enough about Linux networking and file sharing, etc, across the LAN (yet), I can't get the file to _this_ computer (other than email), but I'll take a backup of the file, then comment out all lines except the one you mentioned.

Thanks,

Peter

---

