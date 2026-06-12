---
title: "Kernel performance with sysctl's"
date: 2008-01-22
forum: Apple PPC Users
---

### Post by stream303 on 2008-01-22
Do any of you ppc kernel gurus have any recommended sysctl's to improve the performance of the stock Feisty or Gutsy kernels?

I'm getting too lazy to recompile kernels and wouldn't mind researching or doing some benchmark comparisons if I could be pointed in the right direction.

For example, to look at my current sysctls, I did
```
sudo sysctl -a | sort > readme.txt
```

which I perused and found that my stock Feisty setup on another G5 iMac is using 12288 "kernel.threads-max"

I'm not looking to go crazy, I just want to make sure that my typical desktop-type user environment is doing the best it can.

If anyone has changed any of their sysctls for performance, I'm all ears...

---

