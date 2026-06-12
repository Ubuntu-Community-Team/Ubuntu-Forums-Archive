---
title: "No Splash Theme."
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by DUfire on 2008-04-20
I installed a new splash from GNOME-Look using the Start-Up Manager from Synaptics, and I don't see a splash when I boot.
In fact, when am I supposed to see it? I don't think I've seen a splash screen since I installed the distro.

---

### Post by jakupl on 2008-04-20
try
```
sudo gedit /etc/usplash.conf
```

change from 1280 x 1024 to 1024x768

then run
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by DUfire on 2008-04-20
> **jakupl said:**
> try
```
sudo gedit /etc/usplash.conf
```

change from 1280 x 1024 to 1024x768

then run
```
sudo update-usplash-theme usplash-theme-ubuntu
```

And if I wanna install a different one I use :

```
sudo update-usplash-theme usplash-theme-fingerprint
```

?

I'm gonna try that; will post results.

---

