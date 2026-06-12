---
title: "Xsane"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Hookheathen on 2007-04-16
Help please gurus!

I dual booted Ubuntu 6.10 on to my laptop without difficulty and was very happy with the results. Xsane identified my HP psc 1355 and worked fine. But after a mysterious triplication(?) of Ubuntu in the boot up menu, the computer became understandably a little slow to start but once going would then function fine with the exception of Xsane - it then refused to identify the HP psc. 

With help from this forum, for which many thanks to the guys that responded so quickly with helpful solutions, I have now successfully removed the duplicate UB boot options. However Xsane still will not identify the HP psc. saying "no devices available". I have uninstalled & reinstalled Xsane using Synaptic, as well as installing a new printer, both without success. I have run out of my extremely limited ideas. Hate to be a pest but please could someone advise how to solve this new problem. Many thanks in advance.

---

### Post by leibowitz on 2007-04-25
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

```
sudo /etc/init.d/hopj setup
sudo /etc/init.d/hopj start
```

---

