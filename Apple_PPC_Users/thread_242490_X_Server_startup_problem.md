---
title: "X Server startup problem"
date: 2006-08-23
forum: Apple PPC Users
---

### Post by imageburn on 2006-08-23
A laptop I'm using with Dapper 6.06 was recently unplugged and shutdown due to battery depletion. This was not the first time this has happened, but it is the first time the laptop has rebooted claiming to be unable to properly run the 'X server'graphical interface. A blue splash screen now appears that offers to run a diagnostic to determine the problem. However the diagnostic will not run and instead moves straight to a shell. What is the best way to reinstall X server or whatever and fix this problem? Can I just symantec or update my way to a repair?

---

### Post by mlind on 2006-08-23
This could be caused by recent **xserver-xorg-core** update which broke very many installs in the same way. 
Press Ctrl+Alt+F1 and login with your username and password. Then type
```

sudo aptitude update
sudo aptitude upgrade

```
Accept if aptitude finds any updates. If xserver-xorg-core was included on the upgraded packages list, then after aptitude has upgraded restart gdm/kdm by doing
```

sudo /etc/init.d/?dm restart

```


If no upgrades were found, or this didn't fix your issue, post your /var/log/Xorg.0.log

---

