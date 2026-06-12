---
title: "Virtualbox Error"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Aloush on 2008-04-02
Hello
well i am new to ubuntu and i have just installed virtualbox however when i try to install XP i get the following error

[http://img150.imageshack.us/img150/3006/screenshotim2.png](http://img150.imageshack.us/img150/3006/screenshotim2.png)

Thanks

---

### Post by Whiffle on 2008-04-02
Looks like the kernel module isn't loaded and/or the service for it isn't started.

Do:
sudo /etc/init.d/vboxdrv start

in a terminal

---

### Post by wolfen69 on 2008-04-02
search synaptic for virtual box and install the ose modules, then in terminal: /etc/init.d/vboxdrv start

---

### Post by kellemes on 2008-04-02
Read the hole thing.. it explains how to build/install the kernel modules etc..
[http://ubuntu-tutorials.com/2007/10/12/how-to-install-virtualbox-open-source-edition-on-ubuntu-710/]("http://ubuntu-tutorials.com/2007/10/12/how-to-install-virtualbox-open-source-edition-on-ubuntu-710/")

Edit: or this one.. [https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

---

### Post by Aloush on 2008-04-02
Thanks you guys

---

