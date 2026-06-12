---
title: "Missing ppp modules"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by rozilla on 2006-12-09
i read somewhere that when u check to see which ppp modules are loaded it should show these three:
```
$ lsmod|grep ppp

ppp_generic
ppp_async
ppp_deflate
```


but mine only shows:

```
ppp_generic            30100  0
slhc                    7424  1 ppp_generic
```

how do i get the other two ppp modules loaded? and what's that slhc one do?

---

