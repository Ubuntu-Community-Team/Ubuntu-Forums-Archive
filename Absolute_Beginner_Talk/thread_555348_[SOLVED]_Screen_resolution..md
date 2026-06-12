---
title: "[SOLVED] Screen resolution."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-09-20
Ok, i just got my correct nvidia drivers up and running using the Envy script. It's not in my nvidia settings or in my screen resolution settings. When I rebooted I lost my screen resolution that I had, (1024-786). Is there a way I can get this back.

---

### Post by wolfen69 on 2007-09-20
try this:
in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
make sure to choose the nvidia selection and not nv.

---

### Post by phizikal on 2007-09-20
Amazing, thanks for that by the way.

---

