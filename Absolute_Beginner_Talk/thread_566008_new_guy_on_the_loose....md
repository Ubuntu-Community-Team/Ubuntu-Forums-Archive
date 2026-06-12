---
title: "new guy on the loose..."
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by mtn_man on 2007-10-02
Anyone,

I have installed Ubuntu 6.06.1 (Daper Drake) on a i386 server and am wondering if I can put a Kubuntu desktop (or KDE or GNOME) or some form of a GUI on it and still keep my LAMP server configuration.

I have been reading the online docs and have found out how to install these apps (most examples seems to assume that a UI is installed), but nowhere have I found if the LAMP server config is affected at all by installing a desktop. I would assume that it is OK to do so, but I want to be sure before I try it.

Also, is it best to use the apt-get command to install packages since I currently have only a terminal to work with?

Thanks

---

### Post by w4ett on 2007-10-02
> **mtn_man said:**
> Anyone,

I have installed Ubuntu 6.06.1 (Daper Drake) on a i386 server and am wondering if I can put a Kubuntu desktop (or KDE or GNOME) or some form of a GUI on it and still keep my LAMP server configuration.

I have been reading the online docs and have found out how to install these apps (most examples seems to assume that a UI is installed), but nowhere have I found if the LAMP server config is affected at all by installing a desktop. I would assume that it is OK to do so, but I want to be sure before I try it.

Also, is it best to use the apt-get command to install packages since I currently have only a terminal to work with?

Thanks

I wouldn't think it would cause you any problems, but I might be wrong.

To install the Ubuntu Desktop environment (Gnome)
```

sudo apt-get install ubuntu-desktop
```

you can do the same for KDE and XFCE as well

---

### Post by dpar on 2007-10-03
This may help.....[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

---

