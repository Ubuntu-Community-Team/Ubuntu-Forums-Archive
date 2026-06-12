---
title: "Installing X11"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Cod on 2006-11-09
Hi,
I'm trying to compile an older version of R (v. 2.3.1).  When I run ./configure it falls over with "...X11 headers/libs are not available".  Looking at the installation notes, all it says is:

"you need `X11' installed, including its headers and client libraries. (On Fedora Core Linux this means the `xorg-x11-devel' and `xorg-x11-libs' RPMs, for example. Older Linuxen used `XFree86-'. Some Debian derivatives apparently also require `libxt-dev'.)"

Looking through my installed packages I notice that I have some X11 packages already installed but there are many, many more that I do not have.  Without wishing to just install at random, does anyone know which packages I need?

Thanks

---

### Post by bsussman on 2006-11-09
I **think **xorg-dev may be the right meta-package

---

### Post by Cod on 2006-11-09
Thanks a bunch.  I'll give it a try later.

---

### Post by bsussman on 2006-11-09
> **Cod said:**
> Thanks a bunch.  I'll give it a try later.

Please do post results - I do not like to give out faulty answers!

---

### Post by chemicalnitmare on 2008-01-31
The xorg-dev worked just fine... I did the ./configure on R 2.6.1 on Ubuntu. thanks for the post!

---

