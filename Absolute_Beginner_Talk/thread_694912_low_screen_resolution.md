---
title: "low screen resolution"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by antonyant11 on 2008-02-12
Hi I am brand new to kubuntu. I have loaded the os and graphics drivers for my quadrofx 4600 from the nvidia site. I am unabe to jack my screen res up to the full 2560x1600.  As I am viewing on a dell3007wfp-hc its kinda annoying. can some one please help me?

---

### Post by jaytek13 on 2008-02-12
Can you post your X config file here? The command is

```
kate /etc/X11/xorg.conf
```

And don't change anything in the file, just copy and paste it.

---

### Post by jan quark on 2008-02-12
post your xorg.conf file please
```

cat /etc/X11/xorg.conf
```

do you have tried to reconfigure the xserver?

```
sudo dpkg-reconfigure -plow xserver-xorg
```

---

### Post by antonyant11 on 2008-02-14
thanks for your reply. However I already fixed the problem by running envy to configure my xorg.conf. then upping the resolution using the nvidia settings tam in the start menu.

---

