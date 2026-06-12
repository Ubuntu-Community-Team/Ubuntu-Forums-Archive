---
title: "[SOLVED] change my splash screen"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by shortybookit on 2007-09-18
how do i do it in 7.04 i have compiz and there is no simple option to change the splash screen like there is to change theme or the backgroun

i tried to just download a splash screen and put it in to the splash dir but it says i dont have proper rights...

i am the only user i am admin it is my personal computer

---

### Post by ThrobbingBrain66 on 2007-09-18
You need to install gnome-splashscreen-manager from the repositories.
```
sudo apt-get install gnome-splashscreen-manager
```

Then download a splash screen from gnome-look, or a similar site, and apply it using the above package.  I believe a link is placed in System > Preferences > Splash Screen Manager

While you may be the only user on your computer, it's telling you that you don't have rights because you aren't the administrator on your computer.  To gain temporary administrative rights, you must use sudo (for a terminal app) or gksudo (for a graphical app), and then enter your password.

---

### Post by shortybookit on 2007-09-18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-splashscreen-manager
eric@always-bitchin:~$

---

### Post by Dark Star on 2007-09-18
```
sudo apt-get install gtweakui
```

Has option to change Splash screen under System -> Prefrences -> gtweak session 
++ lots other useful utilities :)

---

### Post by ThrobbingBrain66 on 2007-09-18
[quote=shortybookit]
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gnome-splashscreen-manager
eric@always-bitchin:~$[/quote]

Read my post to you when you asked this same question a while back:
[http://ubuntuforums.org/showthread.php?t=542788](http://ubuntuforums.org/showthread.php?t=542788)

---

### Post by shortybookit on 2007-09-18
there is no Universe repo box to check

---

### Post by FuturePilot on 2007-09-18
You mean you don't see what's in the attached screenshot?

---

### Post by shortybookit on 2007-09-18
ya i see that and i checked that but what you circled said nothing about univ repo???

in any case it works

thank you much:)

---

### Post by Dark Star on 2007-09-18
> **Dark Star said:**
> ```
sudo apt-get install gtweakui
```

Has option to change Splash screen under System -> Prefrences -> gtweak session 
++ lots other useful utilities :)

Haven't you tried this 1 its way better than Splash manager :guitar:

---

