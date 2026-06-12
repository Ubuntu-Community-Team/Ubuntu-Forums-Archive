---
title: "Missing packages"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by shavedaccord on 2007-09-20
Hey guys I'm pretty new to nVidia and Ubuntu. I am trying to use Envy but I am running into a problem. It says I'm missing some packages and I have no idea where to get them? Any help? Below is a paste from Terminal upon trying to install Envy.

> Unpacking envy (from envy_0.9.7-0ubuntu11_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy


---

### Post by Jeroen Vernooij on 2007-09-20
Hi,
try to download this file, and run it. So don't use a terminal. Hopefully it will automatically install the dependencies.
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb)

---

