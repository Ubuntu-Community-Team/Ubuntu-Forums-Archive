---
title: "Ufs"
date: 2012-01-21
forum: Any Other OS
---

### Post by ahso4271 on 2012-01-21
Hi
i think of installing BSD and wonder if UFS is RW enabled or will be in 12.04?
Thanks

---

### Post by kk0sse54 on 2012-01-22
No, write support for UFS in linux is still marked as dangerous in the kernel

---

### Post by Double.J on 2012-01-22
Read support isn't much of a problem with the ufsutils package though. All it really means is that you can't edit the system partition(s) in freebsd to fix problems - it's best to have a shared partition for OS's I find - for reading and repairing freebsd, In the manner of Ubuntu live CD, I tend to use the PC-BSD live USB. 

I won't lie I'd love to have it too, but in real life it isn't that important as long as you have a shared partition - if you've accidentally left something you want on the bsd partition you can still copy it off :)

---

