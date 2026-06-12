---
title: "fatal problem"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by bellzii on 2007-03-17
hey every1 , im using ubuntu 6.10 and just yesterday when i was compiling a package my screen changed black with nothing except a blinking cursor , i had no other option other than to restart and since then after i open the computer it logs onto shell or terminal and theres no interface,  i tried "startx" but i got a green screen with the mouse cursor but theres nothing else in the screen. Can you help me sort this error
thanks for your time

---

### Post by jbayone on 2007-03-17
You may want to reconfigure x by booting in recovery mode then```
sudo dpkg-reconfigure xserver-xorg
```
and then ```
sudo /etc/init.d/gdm start
```

---

