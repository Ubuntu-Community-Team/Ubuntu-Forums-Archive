---
title: "i messed up my xconf and want to start over"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by chronusdark on 2007-11-03
Basically i have butchered my xconf and just want it to autogenerate one like it did when i first installed how do i do this?

---

### Post by haldean on 2007-11-03
```
sudo dpkg-reconfigure xorg xserver-xorg
```
should do the trick.

---

### Post by gate on 2007-11-03
sudo dpkg-reconfigure xorg
 or
sudo dpkg-reconfigure xserver-xorg

 one of those should do it, I think.
 Since you are doing it manually it will ask you alot of questions, try to use the defaults when possible.

  :) Rule #1 of messing with xorg.conf, copy it somewhere safe first.

---

