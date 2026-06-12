---
title: "adept"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-26
Could not launch menu item

Details: Failed to execute child process "kdesu" (No such file or directory)

 i can not open any programs that require kdesu ,adept and a few outhers,
 any help would be great ,thanks  ](*,)

---

### Post by seijuro on 2006-10-26
open a terminal and type kdesu --help to make sure its working/usable by you/etc. if it tells you it doesn't exist try sudo apt-get install kdesu if it is there and working perhaps someone more knowlegeable will post other possible problems.

---

### Post by STREETURCHINE on 2006-10-26
rex@Linux:~$ sudo apt-get install kdesu
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kdesu
rex@Linux:~$


tried to install and got this message :confused:

---

### Post by seijuro on 2006-10-27
sorry for the slow reply had a connection issue anyway I looked a little closer at kdesu and my bad it's not its own pkg the only thing I can think of at this point is maybe try reinstalling kde.
```
sudo apt-get --reinstall install kde-desktop
```

---

### Post by STREETURCHINE on 2006-10-27
no problem ,yes i thought i may have to install kde ,thanks for your help i shall try to install ,hope your connection is fixed,:D

---

