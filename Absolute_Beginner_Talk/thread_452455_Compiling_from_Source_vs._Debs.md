---
title: "Compiling from Source vs. Debs"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by blazercist on 2007-05-23
Is it always better to compile an app from the source?  Whats the difference really?  Is there a difference? What are the advantages/disadvantages of Compiling vs. installing Debs?

---

### Post by lazyart on 2007-05-23
Unless you are going to modify the code, install the .deb.  It's simpler and if there are any dependency issues, you are likely only a```
sudo apt-get install -f
```away from fixing them.  It's cleaner, quicker, leaves less junk and is easier to uninstall.

---

### Post by ruy_lopez on 2007-05-23
There are advantages to compiling software, it optimises the build for your hardware, instead of relying on assumptions. For most uses, though, you'll hardly notice a difference. For most applications, the convenience of installing binary packages over chasing down dependencies is just too great. But if there's a particular application, say a server or something, that'll see heavy use, you should consider compiling from source. Source versions are, obviously, developed ahead of binary packages. So you can use the latest version.

---

### Post by Kobalt on 2007-05-23
Compiling can also be a bit more flexible, it let's you set environment variables, etc. But let's face it, the debian package system is a wonderful tool.

---

### Post by blazercist on 2007-05-23
Kobalt, you and I meet many a time in this forum, answer my other post about fluxbox without fluxbox :D

---

### Post by RedSquirrel on 2007-05-24
> **blazercist said:**
> Is it always better to compile an app from the source?  Whats the difference really?  Is there a difference? What are the advantages/disadvantages of Compiling vs. installing Debs?

When you compile applications yourself, you get more flexibility, but it is more difficult. Using the package managers is very easy, at the expense of flexibility.

When you compile something, you can choose how you want to configure it. When somebody else compiled the application, then you are "stuck" with *their* configuration choices (usually the defaults).

For example, when you run the configure script, you can check the configuration options like this:

```
./configure -h
```and decide what you want to include or exclude. (Most users would probably be satisfied with the defaults, which is why package managers are usually the best option for most users.)

---

### Post by HokeyFry on 2007-09-28
i generally find that installing libraries and such is best left to the package manager of your choosing, and i prefer to compile applications from source.

---

