---
title: "Information from a Gentoo ebuild"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by theharshone on 2008-01-08
Hi,
Can you use the information in a gentoo ebuild to compile the package under ubuntu?
If so, how could i do it?
Thanks

---

### Post by flick on 2008-01-08
A Gentoo ebuild will certainly help you find the source of a given program, tell you what its dependencies are and what architectures it ( probably ) will successfully build on. 

To the best of my knowledge, Portage has not been ported to Debian/Ubuntu, so you can't make direct use of an ebuild.

You can get close to Gentoo's compile-time optimization in Debian/Ubuntu, however. Check out this article on the apt-build utility : [http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

apt-build is in the Ubuntu repos. You can set processor type, cflags, pretty much everything EXCEPT for optional  dependencies ( USE flags in Gentoo ).

Hope that helps at least a little.

---

### Post by theharshone on 2008-01-10
Thanks, but i want to compile my printer driver that only works for amd64 on gentoo (since they have ebuilds). So i should just download the necessary ebuilds and search for the sources in them?

---

### Post by theharshone on 2008-01-10
bump

---

