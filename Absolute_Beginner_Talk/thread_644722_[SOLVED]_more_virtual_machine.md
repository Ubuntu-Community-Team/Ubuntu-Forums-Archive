---
title: "[SOLVED] more virtual machine"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by discoade on 2007-12-19
hi guys Again!

im getting an error saying

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

can anyone tell me how to do this?   :confused:

---

### Post by lvleph on 2007-12-19
You need to add your self to the vboxusers group. Go into System>>Administration>Users and Groups, click on manage groups, scroll down to vbusers, select and click properties, then add the root and your user to the group.

[This link has pictures](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)

---

### Post by hyper_ch on 2007-12-19
```

sudo useradd -G vboxusers USER

```

Replace USER with your username and then you'll have to log off and log back in again for it to take effect.

---

### Post by hopelessone on 2007-12-19
follow:
[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)

after you add yer user i had to reboot for it to work...

VirtualBox is great..!!

---

### Post by discoade on 2007-12-19
All done thank you!:biggrin:

---

