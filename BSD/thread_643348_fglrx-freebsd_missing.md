---
title: "fglrx-freebsd missing?"
date: 2007-12-17
forum: BSD
---

### Post by angryfirelord on 2007-12-17
I'd like to get PC-BSD on my laptop with 1680x1050 resolution on my X1600, but that's only possible with the fglrx driver. I know 3D doesn't build correctly, but all I need is the widescreen support. Since the site is down, are there any other methods of building an fglrx driver on FreeBSD?

---

### Post by Harpalus on 2007-12-17
The open source radeonhd driver works fine. It's available as a port on FreeBSD, and it's in OpenBSD-current. No 3d acceleration or even 2d acceleration yet, it's a brand new driver; but it's created with the full cooperation of ATI, so keep an eye on it. The driver works fine with my x1400. It's not perfect - fullscreen video can stutter sometimes - but for the most part, it's perfectly adequate.

---

### Post by angryfirelord on 2007-12-18
> **Harpalus said:**
> The open source radeonhd driver works fine. It's available as a port on FreeBSD, and it's in OpenBSD-current. No 3d acceleration or even 2d acceleration yet, it's a brand new driver; but it's created with the full cooperation of ATI, so keep an eye on it. The driver works fine with my x1400. It's not perfect - fullscreen video can stutter sometimes - but for the most part, it's perfectly adequate.
Nice. :) Those results are pleasant to hear especially considering the project was started in September. 

Now, before I nuke a partition, is there anything special that has to be done or do I simply compile it from ports and add "radeonhd" to the xorg.conf file?

---

### Post by Harpalus on 2007-12-18
> **angryfirelord said:**
> Nice. :) Those results are pleasant to hear especially considering the project was started in September. 

Now, before I nuke a partition, is there anything special that has to be done or do I simply compile it from ports and add "radeonhd" to the xorg.conf file?

Should be the same method you use to install any other X driver, so I'll assume that's a yes. Haven't used X11 with FreeBSD though, so no guarantees.

---

