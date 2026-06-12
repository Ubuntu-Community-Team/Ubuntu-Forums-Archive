---
title: "slow bootup"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by lucky-one on 2008-04-21
I'm using 7.10 and its aout 5 min. to bootup 

Please tell me how to fix it

---

### Post by jakupl on 2008-04-21
I did this, and it worked perfectly.

open up terminal, write:
```
sudo gedit /etc/usplash.conf
```
change from 1280 x 1024 to 1024x768

then run:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

reboot and see how it works.

---

