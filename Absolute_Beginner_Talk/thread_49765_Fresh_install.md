---
title: "Fresh install"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by memoryleek on 2005-07-17
Well I installed this distro last night, and so far I like it. However, during the install process it did not allow me to set an administrator password. so now installing everthing i have to use sudo dpkg... instead of changing users using "su". When i type "su" and try my password it doesn't work, but when i use "sudo" it does work. How can I change or set an administrator password?

---

### Post by damonw5 on 2005-07-17
[QUOTE=memoryleek]Well I installed this distro last night, and so far I like it. However, during the install process it did not allow me to set an administrator password. so now installing everthing i have to use sudo dpkg... instead of changing users using "su". When i type "su" and try my password it doesn't work, but when i use "sudo" it does work. How can I change or set an administrator password?[/QUOTE]
 See this page for more info: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

If you want to stay as root for more than one command, type:
sudo su

---

### Post by Kvark on 2005-07-17
Open a root terminal instead of a normal terminal.

Alternatively "sudo su" works with your sudo password.

edit: damn damonw5, you're too fast. :-#

---

