---
title: "NIvida help"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Cerealbh on 2007-07-07
install feisty got x server problem problm with my drivers i loaded from cd rom installed the restricted drivers restart, it just loads like kernal and i get get xserver problems i get EE failed to load module "nividia" (module does not exist, 0) ee no drivers avaliable, is there a sudo for the nivida drivers i need to do cuz i can get on the kernal so i think that should work any ideas??

---

### Post by atria on 2007-07-07
You have to install the nvidia drivers.

Check out [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Good luck.

---

### Post by annda on 2007-07-07
if your internet is working install the nvidia driver:
```

sudo apt-get update
sudo apt-get install nvidia-glx
```

otherwise reconfigure x

```
sudo dpkg-reconfigure xserver-xorg
```

if none of that works, post the contents of xorg.conf

```
cat /etc/X11/xorg.conf
```

---

### Post by Cerealbh on 2007-07-07
got it ty, u are my hero

---

