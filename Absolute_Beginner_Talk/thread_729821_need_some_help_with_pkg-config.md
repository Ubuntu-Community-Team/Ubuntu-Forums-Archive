---
title: "need some help with pkg-config"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Flexo82 on 2008-03-20
I have downloaded an updated version of pkg-config because monodevelop 1.0 says it wants pkg-config 0.16 or better and you only get 0.15 wth gutsy. I have downloaded 0.23 and made the classic

```

./configure --prefix=/usr/local/
make
sudo make install

```

but this does not update my pkg-config. Can someone please tell me how to update pkg-config

(i know monodevelop 1.0 does not require an updated pkg-config, but some of the dependancies does)

---

### Post by kpkeerthi on 2008-03-20
You may want to use [checkinstall]("https://wiki.ubuntu.com/CheckInstall") to a create a deb of pkg-config and then install the package to make it synaptic-aware.

---

### Post by spiderbatdad on 2008-03-20
> **kpkeerthi said:**
> You may want to use [checkinstall]("https://wiki.ubuntu.com/CheckInstall") to a create a deb of pkg-config and then install the package to make it synaptic-aware.


+1

---

