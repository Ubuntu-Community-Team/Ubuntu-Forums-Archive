---
title: "Apt system"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by madfrenzy on 2008-03-28
I was wondering if there is a way to save the downloaded stuff via apt-get or automatix so that when I install a new version of ubuntu I save time and just install them rather than downloading then installing them

---

### Post by pedro_orange on 2008-03-28
If you refer to the apt-get manual: [http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

You'll see that apt-get has a -d flag or --download-only. If you enable this flag you will be able to download packages via apt-get but not automatically install there and then.

Example:

```
sudo apt-get -d ubuntu-restricted-extras
```

---

### Post by logos34 on 2008-03-28
[AptOnCD]("http://aptoncd.sourceforge.net/")

But if you upgrade a lot of pkgs will be upgraded too, so you might want the newer versions

---

### Post by jan quark on 2008-03-28
first of all do not use automatix, it can cause severe compatibility issues

I am not sure but you can create a download script via synaptic and add via this script the same downloaded packages to another machine

but you still are going to dowload them

then there is the AptonCD
 [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

---

### Post by madfrenzy on 2008-03-28
thnx alot, this is goood ;)

---

