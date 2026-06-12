---
title: "Resetting Hardware"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-04-01
Recently, I moved my hard drive to another computer. However, the Gnome GUI does not appear and I have immediately redirected to the command prompt. When I installed Ubuntu, it automatically recognised all the drivers for my hardware. What should I do to do the same process as in the setup? Thanks!

---

### Post by trent dillman on 2006-04-01
Well, first thing first, let's get you working in X.

Log in the command line, then do

```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```

---

