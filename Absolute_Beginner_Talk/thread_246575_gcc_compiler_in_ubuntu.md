---
title: "gcc compiler in ubuntu"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by forked_roads on 2006-08-29
i am a beginner. I would like to know how the gcc compiler can be used in ubuntu linux.(i am using the 6.06 release) i wnt to know if the compiler is present or whether it should be installed.

---

### Post by justin whitaker on 2006-08-29
It's in the build-essential package, on the alternate install CD, or via apt/synaptic.

---

### Post by tatimmer on 2006-08-29
On my Breezy install cd, I was looking thru the /pool/g directory and I found 2 compilers, gcc 3.4 and 4.0.  Does anyone know if it really matters what version you install ?

---

### Post by kwalo on 2006-08-29
> **tatimmer said:**
> On my Breezy install cd, I was looking thru the /pool/g directory and I found 2 compilers, gcc 3.4 and 4.0.  Does anyone know if it really matters what version you install ?just install the build-essential package. It'll install the gcc in latest version and other tools needed for compiliation.

Usually you won't need an older version, but if you want to, replace gcc-4.0 with other version, install gcc-3.4 package and do
```
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
```Don't do this, if 4.0 is fine for you!

---

