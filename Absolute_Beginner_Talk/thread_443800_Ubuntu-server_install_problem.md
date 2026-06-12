---
title: "Ubuntu-server install problem"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Ice_Cube[NL] on 2007-05-14
Hi there,

When i try to install the GUI for my ubuntu server it says that it cant find the ubuntu-desktop package.
I used the command "apt-get install ubuntu-desktop".

Can anyone help me?

---

### Post by taurus on 2007-05-14
```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
```

---

### Post by Ice_Cube[NL] on 2007-05-14
ok thnx, it seems to be working now, atleast its now downloading alot of files from the net

---

### Post by taurus on 2007-05-14
Once it's done, try to start GUI login screen with

```
sudo /etc/init.d/gdm start
```

---

