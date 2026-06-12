---
title: "Filesystem Question"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by sandalhat on 2006-09-23
Hello all. I'm somewhat new to everything linux, I've used it before but never extensively. I decided to try to make it my main OS and after a day or two scouring these forums getting all the how-to's on setting up linux I'm left with just a couple of more questions, for the moment at least.

First my filesystem is read only and I havent been able to figure out how to give myself writing permissions. Second if someone would point me in the direction to a thread on how to install java runtime.

Thanx for the help.

---

### Post by bukwirm on 2006-09-23
Most of the filesystem is only writable by the superuser, you can use sudo if you need to - there is an article on permissions [here]("https://help.ubuntu.com/community/FilePermissions").

Do you want the Java plug-in for Firefox or a Java Runtime Enviroment? There should be a JRE installed already.

---

### Post by crokett on 2006-09-23
The official answer on the filesystem is most of it is read only - you should only be saving things in /home and few other spots.  For practicial purposes, read the man pages on chmod and chgrp  in your terminal window type 
```
man chmod
```
```
man chgrp
``` 

Also do a google search on linux permissions to do some general reading.  It takes some getting used to that Windows defaults to more or less letting you do anything you want until the admin stops you.  Linux doesn't let you do anything until the admin lets you. ;)

---

