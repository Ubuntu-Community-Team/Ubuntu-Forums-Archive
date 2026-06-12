---
title: "Serious problem please help"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by K1u on 2007-01-26
After installing ubuntu i installed some/all the stuff from easy ubuntu and automatix including the nvidia drivers.

When i rebooted all the services loads up then all you see is a blank screen, i am typing this from the live cd currently.

Please help.

---

### Post by taurus on 2007-01-26
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
startx
```

---

