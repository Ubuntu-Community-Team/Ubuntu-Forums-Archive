---
title: "ATI Driver problem no GU"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-12-03
I installed the ATI driver.. but it was super super super slow, so i checked it off with the restricted drivers manager but now i dont have a GUI anymore.. how can iget it back:confused:

---

### Post by Snowcat on 2007-12-03
Try reconfiguring xorg with:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by mech7 on 2007-12-31
Ok it works now again with : sudo dpkg-reconfigure xserver-xorg

Only now the performance is even worse then before, is there a way i can revert to the original drivers again ?

---

