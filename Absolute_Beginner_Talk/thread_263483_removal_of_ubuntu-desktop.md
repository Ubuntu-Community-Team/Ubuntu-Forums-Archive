---
title: "removal of ubuntu-desktop"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by KhaaL on 2006-09-23
Hey all

I removed ubuntu-desktop earlier today in order to remove gimp, in favor of gimpshop. My question is, does this bring any negative consequences, for instance in future dist-upgrades or something similiar?

---

### Post by meng on 2006-09-23
No negative consequences. ubuntu-desktop is just a metapackage - lots of dependencies but no substance.

---

### Post by enopepsoo on 2006-09-23
thanks for the info, meng.  I always wondered what that did (and on several occasions decided not to uninstall something because of it.):KS

---

### Post by Perfect Storm on 2006-09-23
But if you want to make a dist-upgrade, you have to install ubuntu-desktop again.

---

### Post by muep on 2006-09-23
Yes, after dist-upgrading, install ubuntu-desktop again if you want to get the current Ubuntu standard apps. After that, you can safely remove that if you want to.

---

### Post by Dec on 2006-09-23
> **KhaaL said:**
> Hey all

I removed ubuntu-desktop earlier today in order to remove gimp, in favor of gimpshop. My question is, does this bring any negative consequences, for instance in future dist-upgrades or something similiar?

How did you get or install Gimpshop? I'm using Drapper.

Thanks!

---

### Post by KhaaL on 2006-09-23
You can get the deb here:
[http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb](http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb)

But make sure to remove gimp and gimp-data before you install it (and of course, ubuntu-desktop will have to poof away too) :)

---

