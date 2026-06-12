---
title: "X server"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by ubuntokun on 2007-11-21
i am trying to run the code:
sudo dpkg-reconfigure -phigh xserver-xorg to solve a problem with my screen resolution at start up and it returns the message [B]/usr/sbin/dpkg-reconfigure : unable to connect to x server 
x is not installed[/B] What does this mean or what should i do I was thinking of reinstalling but I will need help. What do you think guys?:confused:

---

### Post by skyjacker on 2007-11-21
Try the following and see what you get
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Inxsible on 2007-11-21
have you installed the server version by any chance?

---

### Post by ubuntokun on 2007-11-21
What xserver installation??

---

