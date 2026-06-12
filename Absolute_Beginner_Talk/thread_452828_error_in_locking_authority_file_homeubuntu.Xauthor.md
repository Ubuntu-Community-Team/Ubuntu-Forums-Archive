---
title: "error in locking authority file /home/ubuntu/.Xauthority"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by zempter on 2007-05-23
im running a fresh install of ubuntu 7.04 on my dell dimension 2400. i run the cd and get a msg that says something about the xserver. i type in sudo dpkg-reconfigure xserver-xorg and it goes on to the installing components. it finishes that and i type in sudo startx and it doesnt work. i get a message that reads "error in locking authority file /home/ubuntu/.Xauthority" im new with this and have no idea what i am doing. any help would be appreciated also in the message it gives me it says. "fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining. xauth: error in locking authority file /home/ubuntu/.Xauthority"

---

### Post by mlind on 2007-05-23
There's probably xserver instance already running on the default screen.

If you just want to restart xserver after editing xorg.conf, use
```

sudo /etc/init.d/gdm restart

```
or
```

sudo invoke-rc.d gdm restart

```

---

