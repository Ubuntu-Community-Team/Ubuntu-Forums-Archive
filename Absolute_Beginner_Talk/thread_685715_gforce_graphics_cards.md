---
title: "gforce graphics cards"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by markglover12 on 2008-02-02
hi there i recentley had installed a gforce mx440se 64mbddr. i have just bought a gforce tornado 5200 256mb(128bit) ddr but now its installed my unreal tournement and quake 3 dont seem to be running like they did please help someone

---

### Post by Faud on 2008-02-02
Do you have the restricted drivers installed ?

---

### Post by jan quark on 2008-02-02
you can also use the application envy to install drivers for nvidia cards
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Nythain on 2008-02-02
the craptastic 440 was probably running nvidia-glx-legacy... you need either nvidia-glx or possibly nvidia-glx-new... i would probably go with just plain old glx to be on the safe side
```

sudo dpkg --purge -r nvidia-glx-legacy
sudo aptitude install nvidia-glx

```
should hopefully do the trick
after that might need a
sudo nvidia-settings --enable or whatever the command is, or you can just look at your xorg and make sure its using nvidia and not nv

---

