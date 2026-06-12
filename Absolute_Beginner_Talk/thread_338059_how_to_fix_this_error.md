---
title: "how to fix this error"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by broekskw on 2007-01-13
ok everytime i got to the add&remove application and reload i keep getting this error. does someone have a fix for this, must be an invalid string line ???:D

---

### Post by %hMa@?b&lt;C on 2007-01-13
sudo gedit /etc/apt/sources.list
remove the line with the repository from "albertomilone.com"

---

### Post by Sef on 2007-01-13
> sudo gedit /etc/apt/sources.list
remove the line with the repository from "albertomilone.com"

Use > **gksudo** gedit /etc/apt/sources.list

Using sudo can break your system,  if you use it to start a graphical program, such as gedit.  See [RootSudo]("https://help.ubuntu.com/community/RootSudo") for more information.

---

