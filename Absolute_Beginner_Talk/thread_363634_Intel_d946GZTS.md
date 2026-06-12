---
title: "Intel d946GZTS"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by regard on 2007-02-17
Hi I upgraded to Ubuntu recently, I am still trying to figure out how and what but it is good fun.

The Challange:
I installed ubuntu on an Intel D946GZTS motherboard with onboard graphics and that went fine.
the screen resolution was ok.

I did all the updates, and I have confirmed that my pc is up to date.
and after rebooting my screen resolution is 640x480, and I dont have any other options available.

any Ideas?

Thanks

---

### Post by regard on 2007-02-17
I am not 100% sure if it is a D946GZIS or D946GZTS board..
is there a terminal command to find that info?

---

### Post by regard on 2007-02-18
i think I may have found the answers, they come from intellinuxgraphics.org


Source Code and Precompiled Binaries
Compiling and/or upgrading video drivers in Linux is a complex and error-prone task. If you are not experienced doing this, we recommend that you get precompiled packages from one of the many Linux distributions.

Source code repositories
X.org 2D driver
The Intel driver for X.org is available from the public X.org git repository:

$ git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel

DRM kernel module
The DRM kernel modules are available from the public DRM git repository:

$ git-clone git://anongit.freedesktop.org/git/mesa/drm

Mesa 3D GL driver
The GL drivers are available from the public Mesa git repository:

$ git-clone git://anongit.freedesktop.org/git/mesa/mesa


ok does any one know what that means the first one I can do..
but I havent learned the rest any ideas?

---

### Post by Xceptiona1 on 2008-02-26
I was looking at the same website/link and wondering if that would help me. I already downloaded/installed the backport driver, which partially enabled 3d, but was hoping this would fully enable it.

---

