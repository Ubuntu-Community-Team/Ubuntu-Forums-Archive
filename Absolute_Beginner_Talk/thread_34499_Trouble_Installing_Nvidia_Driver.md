---
title: "Trouble Installing Nvidia Driver"
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by BearnaN on 2005-05-15
Hey im completly new to linux and im tyrin to install the Driver for my Nvidia graphics card and it keeps sayin this when im trying to install "ERROR:You appear to be running a X server; Please exit X before installing"   what is X and how do i Exit it?

---

### Post by Knome_fan on 2005-05-15
X (or rather the X server) is the base of any graphical environment in Linux. To exit it, log out of Gnome, than change to a console (ctr+alt+F1), log in (type your username and then your password) and stop the gnome desktop manager:
sudo /etc/init.d/gdm stop

However, you don't have to do this, as the nividia driver is also provided by Ubuntu:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

Hope this helps.

---

### Post by BearnaN on 2005-05-15
THANKZ!!!! Knome i got it working  :grin:  :grin:  :grin:

---

