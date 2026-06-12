---
title: "updating from 6.10 to 7.04"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Pitwolf45 on 2007-08-04
I've tried to update using command line and will not read dvd or cd. Then I went to admin side and would not allow me to apt get update either what should I do....Would like to clean install and try again....any help.

#apt-get -u dist -upgrade or # apt-cdrom add

I've been using the program for about 2 weeks, I know I havent enought time using it...Should be a simple way to upgrade

---

### Post by sad_iq on 2007-08-04
Try ```
sudo aptitude update && sudo aptitude dist-upgrade
``` Post your sources.list if you run into trouble: ```
gksu gedit /etc/apt/sources.list
```

---

### Post by luisromangz on 2007-08-04
Here is an article that explains how to upgrade to Ubuntu 7.04 from 6.10, both using GUI and from the command line interface.

[http://www.debianadmin.com/how-to-upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn.html]("http://www.debianadmin.com/how-to-upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn.html")

Summarizing, you change the repositories listed in /etc/apt/sources.list, then perform an apt-get update, and then an apt-get dist-upgrade, always with admin privileges.

You should be able to upgrade happily.

---

### Post by Pitwolf45 on 2007-08-04
Thx for the help I will try it

---

### Post by shearn89 on 2007-08-04
> **Pitwolf45 said:**
> 
#apt-get -u dist -upgrade or # apt-cdrom add


You definitely have to put "sudo" at the front, unless you've logged in as root user. It should also be "dist-upgrade" not "dist -upgrade", and i've no idea what the -u flag does...

---

### Post by Sbarton on 2007-08-04
Theres lots of tutorials about upgrading, have a look at this one:
[http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/](http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/)
regards

---

