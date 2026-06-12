---
title: "GDM to KDM problems"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by csonja on 2007-04-08
Hey,

I was using GDM before and decided to switch to KDM, which I did by editing /etc/X11/default-display-manager and putting there /usr/bin/kdm

But now, when the system boots, and when there should be the login screen loaded, there is only a black screen instead. I can get to KDM login screen by pressing ENTER and ALT+F7. But it is annoying to do it every time, especially when one is in a hurry... 

Anyone that could help, please?

Thanks

---

### Post by teaker1s on 2007-04-08
try
```
sudo dpkg-reconfigure kdm
```

see if dpkg can fix the config

---

### Post by csonja on 2007-04-08
i did try it, and nothing happened

---

