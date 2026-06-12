---
title: "Canon IP1500: Dependency problem"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by owler on 2006-08-10
Hi,

I'm trying to make my Canon Pixma IP1500 printer work with my system Ubuntu 6.06, since the ip1500 driver isn't default on print manager. So i found a couple tutorials to help.

One of them ask to install 3 .deb files:

[COLOR="Orange"]bjfilter-common_2.50-3_i386.deb
bjfilter-pixmaip1500_2.50-3_i386.deb
bjfilter-pixmaip1500-lprng_2.50-3_i386.deb[/COLOR]

Thoses files are supposed to be the needed driver to make my printer work on Ubuntu. Of course, there's a cpl dependencies related to them and one in particular gave me hard time.

[COLOR="Orange"]libcupsys2-gnutls10[/COLOR]

When i try to install it, system return an error message:

```
libcupsys2: is conflicting with: libcupsys2-gnutls10 (<= 1.1.23-11)
```

Q 1.[INDENT]Should I remove libcupsys2 to install libcupsys2-gnutls10 ?[/INDENT]

Q 2.[INDENT]If answer to Q 1. is no, there is another way to fix this dependency conflict to reach my objective concerning my Canon printer ?[/INDENT]

Thanks for helping,

owler

---

### Post by John.Michael.Kane on 2006-08-10
If removing libcupsys2 allows the install of libcupsys2-gnutls10 which i take it is the file cannon is calling for. there should be no problems. also is this on an install of dapper or brezzy?

---

### Post by owler on 2006-08-10
> **SD-Plissken said:**
> If removing libcupsys2 allows the install of libcupsys2-gnutls10 which i take it is the file cannon is calling for. there should be no problems. also is this on an install of dapper or brezzy?

It's a Dapper install. But I think I will not need to take risk replacing libcupsys2 with libcupsys2-gnutls10 because i just found a script from a user [here]("http://www.ubuntuforums.org/showthread.php?t=93265&highlight=canon+drivers") that seem to work perfectly. At least it allow me to print the test page with my Canon ip1500. I'll make further test but looks good for now.

Thanks for your help and the friendliness of this whole community.

---

### Post by John.Michael.Kane on 2006-08-10
Well I'm glad you was able to find a suitable fix. please post should you have any other issues.

---

