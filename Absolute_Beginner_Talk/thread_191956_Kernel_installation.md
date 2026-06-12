---
title: "Kernel installation"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by pjeeanah on 2006-06-08
How do I install an smp kernel on my breezy installation? I am using a an intel86X_64 with hyperthreading. I see that the kernel is a only 686 and not smp. I have only the i386 version of breezy installed.

Thanks for your help.

---

### Post by Jagot on 2006-06-08
In terminal:

```
sudo aptitude install linux-686-smp
```

Alternatively you could go to Synaptic and do it from there.

---

