---
title: "Xserver Crashing"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-22
Hello,
Xserver crashes each time boot edgy.&#9618;¿!¿!¿!](*,) ?!?!?&#9618;
I tried the command "sudo dpkg-reconfigure xserver-xorg".
But the default resolution is too low and i dont even get full screen at 1024*648.
Each time i update my nvidia 6600 drivers, xserver crashed again.
Is there a way to reconfigure that xserver to it initial state, similar when u make fresh install or is there a way to solve the issue.
thanks

---

### Post by taurus on 2006-11-22
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

