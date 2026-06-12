---
title: "cant open desk top"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by sublimeprogie on 2006-07-09
hi, i am completely new to linux in any shape or form, i have installed ubuntu and can log in ok, but i dont know how to get into my desktop.  i have tried startx, sudo startx, and startkde, as referenced from another source but none of these worked 

i would like to get into the desktop so i could learn more about linux without having to switch into my mac os

thanks for any help

sp

---

### Post by catlett on 2006-07-09
You may have installed the server version which doesn't have a desktop. Use these commands and 1 of 2 things will hapen. Either you have it installed and notrhiung will bew done or it will install a desktop.

If you want the regular Ubuntu with gnome as the desktop enter this command ```
sudo apt-get install ubuntu-desktop
```If you want Kubuntu with kde as your desk top, enter this```
 sudo apt-get install kubuntu-desktop
```

If you only had the server edition this command will install the desktop. After it installs reboot and it will start up on it's own or enter startx

---

### Post by aysiu on 2006-07-09
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) has some more tips.

---

