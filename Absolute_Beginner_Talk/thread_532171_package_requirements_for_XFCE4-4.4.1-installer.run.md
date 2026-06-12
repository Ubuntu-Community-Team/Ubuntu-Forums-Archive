---
title: "package requirements for XFCE4-4.4.1-installer.run?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Caermundh on 2007-08-22
I have downloaded xfce4-4.4.1-installer.run from the sourceforge mirror and am attempting to install it on an ubuntu 7.04 alternate install system. I had to install libgtk2.0-dev and libxpm-dev before i could run the graphical interface. Once i had that running, i still had to install libxml2-dev and libvte-dev before i met all of the "mandatory dependancies" listed by the installer. I also noticed that installing libdbus-glib-1-dev let me meet one or two of the "optional dependancies" that hadnt been met yet. However there are still several items under optional dependacies that say they are not met yet. I know that i dont HAVE to meet these requirements to install XFCE, however i would very much like to do so, just to ensure that xfce has every last thing it could possibly need.

The dependancies that arent being met are: libstartup-notification-1.0, hal-storage, xcomposite, xdamage, and jpeg (under Libraries). What pacakges do i have to apt-get install in order to meet these requirements?

---

### Post by wolfen69 on 2007-08-22
to install xfce, you could have done:
```
sudo apt-get install xubuntu-desktop
```
done.

---

