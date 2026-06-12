---
title: "wine error"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by dr.silly on 2007-07-03
```
sam@sam-desktop:~$ wine notepad.exe
wine client error:14: version mismatch 304/306.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```

what? I followed instructions on wine website

---

### Post by Rocket2DMn on 2007-07-03
You should get wine from the repositories instead of compiling it yourself from their website, there is better support and reliability when you use the repos.
```
sudo apt-get install wine
```

---

### Post by cogadh on 2007-07-03
However, if you want to use the latest version, Wine does have its own Ubuntu repository, so you can install those packages without having to compile from source:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

