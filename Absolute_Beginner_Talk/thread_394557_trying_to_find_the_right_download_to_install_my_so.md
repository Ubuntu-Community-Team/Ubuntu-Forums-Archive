---
title: "trying to find the right download to install my sound card"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by newmanfan on 2007-03-27
i have a compaq deskpro en 6266 that i m trying to install a media player on but it wont let me because it cant find my souncard which it say is a nvidia and after openning see it is not but still unsure can not find any drivers my ubuntu 5.10 )upgraded via internet to 6.06) will install or get to work. i m semi computer stupid so it mite take a little bit to get me where i want to be.

---

### Post by zvacet on 2007-03-27
```
sudo gedit etc/X11/xorg.conf
```

you will find there wich is your video card

```
 sudo dpkg-reconfigure xserver-xorg
```

pick your graphic card

---

