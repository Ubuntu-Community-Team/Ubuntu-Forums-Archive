---
title: "editing configurations"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by rjdizz63 on 2007-11-30
i am very new to this and i am trying to configure the FTP server etc and the directions stay to /etc/vs etc but i dont know how to get to the editing screen. does any understand what i am talking about

---

### Post by wormser on 2007-11-30
It sounds like you are just trying to edit the configuration file.  Nano is a program that edits with in your shell window. If you are trying to edit /etc/vs, use the following command:

```
sudo nano /etc/vs
```

If you want to do the same in a graphical application:

```
gksudo gedit /etc/vs
```

Sudo give you root priviledges for shell applications and gksudo does the same for graphical applications.

---

