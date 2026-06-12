---
title: "How to make a deb package"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-05-27
I have been looking on ways to make a deb package, with its respective dependency as requirements.   Mostly I am looking into creating a package that I can use to install many other packages (apache2, mysql, phpmyadmin, etc...)  and to copy files to user's desktops, set config files, etc...

Any good software to put it all together?  Hopefully one with a simple GUI, but not required.

---

### Post by Happy_Man on 2007-05-27
Well, there is a command-line app called "checkinstall" if you're compiling from source.....
```
sudo apt-get install checkinstall
```

Not sure what you're asking for, though, so that may or may not be it.

---

