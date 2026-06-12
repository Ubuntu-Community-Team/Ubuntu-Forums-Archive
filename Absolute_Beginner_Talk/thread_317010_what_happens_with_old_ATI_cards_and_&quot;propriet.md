---
title: "what happens with old ATI cards and &quot;proprietary&quot; 3D?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by linuxeiro on 2006-12-11
Hi everybody,   I have an "ATI Radeon 9800 Pro" video card. Getting the proprietary ati driver to work with 3D acceleration has been impossible for me since I started using Ubuntu back in 5.04 (I use 6.10 nowadays).  I was happy with M. Shuttleworth decision to make that drivers available during install with 7.04, but reading through the forums I realize that my period of happiness might be shorter than expected, since ATI supports "modern" cards only (9500 upwards).  Does that mean that, in a couple of kernel releases, my ATI card won't be supported? No 3D acceleration ever? will I at least be able to continue using Ubuntu with my "old" ATI card in a couple of years?

---

### Post by Colonel Kilkenny on 2006-12-11
You can use either fglrx-drivers which are ATI's or radeon-drivers which are open source. At some point ATI (or AMD) will drop support for 9xxx-series from fglrx-drivers and then you must either use old fglrx-drivers or switch to open source drivers.
With both drivers you get 3D acceleration, the open source drivers tend to be a little slower (obviously).

---

### Post by xabbott on 2006-12-11
> ...will I at least be able to continue using Ubuntu with my "old" ATI card in a couple of years?

In short...yes.

---

### Post by linuxeiro on 2006-12-11
thank you for your swift answers! ;)

---

