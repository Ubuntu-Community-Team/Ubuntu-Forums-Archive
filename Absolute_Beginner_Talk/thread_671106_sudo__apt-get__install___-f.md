---
title: "sudo  apt-get  install   -f"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-01-18
When I run:  sudo  apt-get  install  -f

I get this:

 trying to overwrite `/usr/lib/mono/gac/ByteFX.Data/0.7.6.2__0738eb9f132ed756/ByteFX.Data.dll', which is also in package bytefx-data-mysql
Errors were encountered while processing:
 /var/cache/apt/archives/libmono-bytefx0.7.6.2-cil_1.2.4-6ubuntu6.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried removing the ByteFX.Data.dll file but still get this error.

Carl

---

### Post by Golem XIV on 2008-01-18
Try removing the whole package libmono-bytefx0.7.6.2-cil_1.2.4-6ubuntu6.1_all.deb

```
sudo rm /var/cache/apt/archives/libmono-bytefx0.7.6.2-cil_1.2.4-6ubuntu6.1_all.deb
```

and then try the apt-get line again

---

