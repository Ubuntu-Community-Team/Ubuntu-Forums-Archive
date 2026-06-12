---
title: "libc6_2.3.5-6_i386.deb install"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by dcast on 2005-10-24
I am trying to install libc6_2.3.5-6_i386.deb. I was trying to install gstreamer0.8-mad but it is dependent on some packages which seem to be dependent on this. When I use dpkg I get

libc6 conflicts with initrd tools (version 0.1.77ubuntu3) is installed

what is initrd tools and how can I fix this problem?

---

### Post by mlomker on 2005-10-24
Do not replace libc6 !!!  Your system will be seriously borked if you do.  Almost everything on the system depends upon the version that Ubuntu provides.

Whatever you are trying to install you will have to compile from source instead.

---

### Post by dcast on 2005-10-24
why would it affect my system to use an updated version of whats already there?

---

