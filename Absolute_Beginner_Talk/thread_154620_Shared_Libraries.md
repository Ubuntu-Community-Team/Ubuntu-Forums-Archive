---
title: "Shared Libraries"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by flabbas on 2006-04-03
Im trying to run a dedicated server, but when I launch it, it throws up this error:

```
error while loading shared libraries: libstdc++.so.5 no such file
```

from a quick google it seems i need to install a shared C++ library (im using an x86 machine, 32bit)

I've found this repository, but im a bit unsure as to which one I should download

[Clicky]("http://rpmfind.net/linux/rpm2html/search.php?query=libstdc%2B%2B.so.5")

any help would be appreciated

---

### Post by localzuk on 2006-04-03
you do not need to use any other repos. Take a look at [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) for info on the default repositories. (or [https://wiki.ubuntu.com/CommandLinePackageManagement](https://wiki.ubuntu.com/CommandLinePackageManagement) if you don't have a graphical display).

The file you want to install is called libstdc++5, so to install this you should type ```
sudo apt-get install libstdc++5
``` (after having ran apt-get update).

---

### Post by flabbas on 2006-04-03
that sorted it - cheers

on a side note, im having some trouble with my net connection - Im fairly certain that Ubuntu is trying to use a protocol not supported by my router.

I've already disabled IPV6 and that sorted a problem i was having with bringing in web pages, but every now and again it hangs while connecting to security.ubuntu.com (when running apt-get)

For the time being i have commented out the security.ubuntu.com servers from sources.list

Any ideas?

---

