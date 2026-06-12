---
title: "Adding to PKG_CONFIG_PATH Variable"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by RedKing on 2005-11-27
First post, and taking my first linux steps...

I am trying to installl and configure software on Breezy.
When i run './configure' i get the following:

Package gtk+ -2.0 not found in the pkg_config search path. perhaps you should add the directory containing 'gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable no package 'gtk+-2.0' found.

I had a look around the filesystem and found gtk-2.0 in /etc/gtk-2.0 , I hope this is the one required by the software?

If it is then i suppose my question is where and how do i edit the PKG_CONFIG_PATH environment variable so that it can be found?

Thanks in advance

---

### Post by ssam on 2005-11-27
do you really need to compile this? [http://help.ubuntu.com/starterguide/C/ch02.html](http://help.ubuntu.com/starterguide/C/ch02.html)

you probaly need to install the gtk dev packages, search for gtk in synaptic and you should find them.

---

