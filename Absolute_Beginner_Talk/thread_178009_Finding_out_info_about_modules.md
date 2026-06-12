---
title: "Finding out info about modules"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by KiranF on 2006-05-17
I'd like to be able to find out info about the modules installed on my computer, or other things. For instance, I would like to know what version of x.org and what linux header versions i have.

On a somewhat related note, the reason i want to find out is i would like to upgrade to linux headers 686, but i don't know if i already have it. Thanks!

---

### Post by kabus on 2006-05-17
For modules try the lsmod and modinfo commands.

---

### Post by KiranF on 2006-05-17
ok, thanks!

---

### Post by xtacocorex on 2006-05-17
For the kernel version info:
```
uname -r
```

I don't know about the Xorg version info, but I think in Synaptic you might be able to find it.

---

