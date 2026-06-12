---
title: "Roll back Video VGA Driver"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by luckymancvp on 2008-03-20
I have just select wrong video card. Before it Ubuntu can display Xdesktop. Now I can't enter Xdesktop. Help me roll back.

---

### Post by kpkeerthi on 2008-03-20
What graphics card do you have?

Boot into recovery mode and post the output of below command
```
lspci
```

---

### Post by keratos on 2008-03-20
Well arch linux is a little more "hands on"

Can you get to a command prompt, i.e. log in and enter your password then "su" enter, then enter the root password.

See if you can copy the old xorg.conf file (includes video card selection)

```
copy /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

In debian based distros, we simply do:
```
dpkg-reconfigure -phigh xserver-xorg
```
and its as easy as that, but not sure on Arch.

---

### Post by luckymancvp on 2008-03-20
Thanks.I will restart and try without CD and type command.

---

