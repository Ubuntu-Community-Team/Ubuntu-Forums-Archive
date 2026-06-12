---
title: "Apt is broken"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by shadow-of-sin on 2008-01-19
I tried installing libmagic1 from a deb file and it failed- now when I try use apt, I get this error message:
```
The following packages have unmet dependencies:
  file: Depends: libmagic1 (= 4.21-1) but 4.23-1 is installed
  libmagic1: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is installed

```

When I try and fix the broken packages in synaptic or use sudo apt-get install -f, I get this error message:
```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

Anyone know how to fix this?

Thanks in advance,

---

### Post by Ub1476 on 2008-01-19
Have you gone into Synaptic, removing it, then installing it again?

Why were you trying to install it via a .deb file anyway when it's in Synaptic?

---

### Post by xeth_delta on 2008-01-19
> **shadow-of-sin said:**
> I tried installing libmagic1 from a deb file and it failed- now when I try use apt, I get this error message:
```
The following packages have unmet dependencies:
  file: Depends: libmagic1 (= 4.21-1) but 4.23-1 is installed
  libmagic1: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is installed

```

When I try and fix the broken packages in synaptic or use sudo apt-get install -f, I get this error message:
```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

Anyone know how to fix this?

Thanks in advance,

You may want to try "sudo apt-get autoclean" and "sudo apt-get autoremove" Look carefully at what would be about to be removed, and accept *only and only if* you are sure.

---

### Post by shadow-of-sin on 2008-01-19
@Ub1476- I would do that but if I remove libmagic then I would remove alot of other packages including compiz and xserver-xorg-core.

@xeth_delta- the first command works but the second produces the same error that I posted above

---

