---
title: "preventing xserver from loading"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-08-27
Out of curiosity, how do I prevent the GUI (GNOME) from loading at startup so that I'm left with a command line? Is there some key to press like in windows where you press F8 for save mode?

---

### Post by bodhi.zazen on 2006-08-27
> **k94382 said:**
> Out of curiosity, how do I prevent the GUI (GNOME) from loading at startup so that I'm left with a command line? Is there some key to press like in windows where you press F8 for save mode?
Several optins here.

1. Remove GDM (he he he...)

2. Manual method. Your start up scripts are in /etc/rc*.d where the * is 1-6, which are the run levels. Ubuntu boots to inint 2 by default. Thus:
```
sudo mv /etc/rc2.d/Sgdm /etc/rc2.d/sgdm
```
Note the change is from Sgdm to sgdm.

3. Install BUM
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

4. Use update-rc.d
```
sudo update-rc.d gdm start 13 345 . stop 13 126 .
```

See also this page:
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Well that is 4. There are other methods.

---

### Post by bodhi.zazen on 2006-08-27
I suppose I should add:

To start GMD:
```
sudo gdm
```

---

