---
title: "uninstalling programs?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by hamirets on 2006-11-30
hi all, sorry my dumbness

i would like to know how to uninstall those programs installed by '.configure-make-make install'

thanks :)

---

### Post by yabbadabbadont on 2006-11-30
Try "make uninstall" in the same directory in which you did "make install".

In the future, try using the "checkinstall" package.  It is in the repos and is simple to use.  You just, "configure", "make", "checkinstall".  It will create a deb package of the software you are building and will then install it for you.  By the way, if my suggestion above of "make uninstall" doesn't work, install checkinstall and use it to re-install the software you built.  Then you can use apt, dpkg, or even synaptic to remove it.  (It should just overwrite the files it installed originally)

---

