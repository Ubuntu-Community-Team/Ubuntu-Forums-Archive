---
title: "Help with error message"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-01-30
Hi all,

I'm trying to get compiz fusion installed on my Feisty desktop. I've run into an issue with (what appears to be) a broken package, and I'm hoping someone can help.

When I run the following in a terminal:
```
sudo apt-get install -f
```

It returns the following:
```
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas?

---

### Post by JoshuaRL on 2008-01-30
Alright, go into Synaptic and search with the broken filter.  Check anything there for installation and let it do it's thing.  Synaptic is really good at fixing broken dependencies.

---

### Post by ~LoKe on 2008-01-30
Package conflict.  Open up Synaptic (**gksu synaptic**) and click on "Custom Filters" at the bottom right, and then "Broken" on the list on the left.  You should be able to select all the broken packages and mark them for re-installation/removal.

---

### Post by doctorbighands on 2008-01-30
Okay, I tried to let Synaptic work for me, and it couldn't. It returned the following:
```
E: /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
```

---

### Post by doctorbighands on 2008-01-30
Nevermind. I believe I've solved the problem on my own.

Thank you!

---

### Post by JoshuaRL on 2008-01-30
What did you do?  Because I'm having the same issue with some stuff I installed in Linux Mint.

---

