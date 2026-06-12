---
title: "connect as root"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by killerfrog on 2006-10-10
Hello,

How is it possible to run "su" in console or to login as root as graphical mode ??

I never had the chance to create a root user during installation and console don't let me connect as su!!!!!!! I need this to edit conf of X11...

Thx

---

### Post by meng on 2006-10-10
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2006-10-10
It's extremely unnecessary.

If you want a root terminal, type ```
sudo -i
``` If you want drag-and-drop root, press Alt-F2 and type ```
gksudo nautilus
``` Those methods are far more convenient than enabling the root account.

For more details:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

If you're comfortable with the terminal, you can edit /etc/X11/xorg.conf with this command: ```
sudo nano -B /etc/X11/xorg.conf
```

---

