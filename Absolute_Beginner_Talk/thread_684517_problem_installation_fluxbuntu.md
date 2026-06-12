---
title: "problem installation fluxbuntu"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by isabelle8274 on 2008-02-01
i have installed fluxbuntu (i386, 7.10  cd from ikarios), the installation seems to be ok but when i start my computer (portable dell inspiron 1100) i only have a blank screen with this message : ubuntu 7.10 fluxbuntu tty1
fluxbuntu login:
password :
i log , then i just have this message :
isa@fluxbuntu:$_
what should i do Doc ?
(excuse my bad english, i'm french but i haven't found any french forum on fluxbuntu)

---

### Post by Odd-rationale on 2008-02-01
Try typing this command after you login and see if this works:
```
init 3
```

If that doesn't work, try
```
sudo startx
```

---

