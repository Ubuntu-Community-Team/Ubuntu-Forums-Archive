---
title: "desktop effects not giving me the top bar on windows"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-07-27
i used to be able to enable them and everything was fine up til ttoday i can close or reze my windows help pleas e i have a nvida feforec fx 5200

---

### Post by rich.bradshaw on 2007-07-27
It's a well known problem. Can't remember the fix, but it will def be in this forum somewhere.

I'd go with Compiz Fusion instead - no more development is being done on Compiz (which is what Desktop Effects is), Compiz Fusion is the newest.

Theres a tutorial on here on how to install.

---

### Post by PurposeOfReason on 2007-07-27
in your xorg.conf file, under the device section, add

```
    Option         "AddARGBGLXVisuals" "True"
```

Of course make a backup first just in case. You never know. Leaving an extra " when doing resolutions has gotten me before.

---

### Post by llzero1337 on 2007-07-27
> **rich.bradshaw said:**
> It's a well known problem. Can't remember the fix, but it will def be in this forum somewhere.

I'd go with Compiz Fusion instead - no more development is being done on Compiz (which is what Desktop Effects is), Compiz Fusion is the newest.

Theres a tutorial on here on how to install.

um where is the tut?

---

