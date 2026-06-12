---
title: "ignorant about linux, not so much about osx and windows"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by irunwithknives on 2008-02-06
I am decently pro at working tiger and XP, but I have mass problems with linux.
I cant install programs, I get a window that says 
"The list of applications is not available
Click on 'Reload' to load it.  To reload the list you need a working internet connection."
and I have working internet.  THere are other things I have trouble with, but this is what is most troublesome at the time.

---

### Post by Tekno_Cowboy on 2008-02-06
you should post your config, and give a little more detail, then someone should be able to help you more. If you know the package name, run this

```
$ sudo apt-get update
$ sudo apt-get install 'yourpackagegoeshere'
```

---

### Post by szymon_g on 2008-02-06
.......... or use aptitude instead of apt-get.
it (by default) download a little more packages, but can handle it when you wanna uninstall it (i.e. application).
for searching for packages, type

apt-cache search your_phrase (you dont need to use it with sudo)

---

### Post by oedha on 2008-02-06
what is in your /etc/apt/sources.list ?
or
go to system - administration - software sources
mark the boxes....!

---

