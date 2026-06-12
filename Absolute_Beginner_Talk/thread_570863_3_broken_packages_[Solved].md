---
title: "3 broken packages [Solved]"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Namingishard on 2007-10-08
When I try and update it says I can't because I have 3 broken Packages,
I went to Synaptic and hit "Fix Broken Packages" and then Apply.
Once that goes for a few seconds I get this error

```
E: /var/cache/apt/archives/libawn0_0.1.9-1+bzr20071006~3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
```

The broken packages according to Synaptic are Avant-Window-Navigator and awn-core-applets.

---

### Post by Pumalite on 2007-10-08
You might want to try:

sudo dpkg --remove --force-remove-reinstreq Avant-Window-Navigator

sudo dpkg --remove --force-remove-reinstreq awn-core-applets

Then re-install if need be

---

### Post by Namingishard on 2007-10-08
Thanks, That worked great.

---

### Post by Pumalite on 2007-10-08
You are welcome. Good luck.

---

