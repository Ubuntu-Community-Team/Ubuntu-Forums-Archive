---
title: "Broken Package!"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Charlatat on 2006-05-09
Update Manager couldn't complete an update and told me to run Package Manager. So I did, and tried the "Fix Broken Packages".  I got this error:

E: /var/cache/apt/archives/libfame0_0.9.0-0unofficialubuntu1_i386.deb: trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame-0.9

Anyone know what's the deal?  Thanks

---

### Post by Hallavej on 2006-05-09
Any unofficial repositories in your /etc/apt/sources.list ?
Looks like an unofficial version of libfame is trying to overwrite the official one.

---

### Post by Charlatat on 2006-05-09
Yup, I do. Hmm...  wonder which one is giving me the troubles...

---

