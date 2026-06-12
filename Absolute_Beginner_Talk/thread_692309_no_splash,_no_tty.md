---
title: "no splash, no tty"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-02-09
when i boot i have a black screen until i have to login.
never used to happen.

also when i push CTRL + F1 for example my screen turns off =(

anyone have any clues?

---

### Post by sheazar on 2008-02-09
What ubuntu are you running?
you could try the command
```
sudo dpkg-reconfigure usplash
```
that solved my problems.

Also you can check the resolutionssettings in /etc/usplash.conf

---

