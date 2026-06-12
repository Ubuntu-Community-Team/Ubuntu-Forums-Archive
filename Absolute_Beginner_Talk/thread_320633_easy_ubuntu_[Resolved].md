---
title: "easy ubuntu [Resolved]"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2006-12-17
Merry Christmas!

While trying to use easy ubuntu it  says it needs my permission to install things.
I don't no how to grant these permissians, it gives me a window with all the programs I want installed but no other options.
what do I do?

---

### Post by aysiu on 2006-12-17
You appear to be a Feisty Fawn user. I don't know if Easy Ubuntu is available for Feisty yet.

These are the instructions from [the Easy Ubuntu website](http://easyubuntu.freecontrib.org/get.html): > NOTE: After you download EasyUbuntu and/or do the automatic update, PLEASE run the following commands: ```
wget http://easyubuntu.cafuego.net/969F3F57.gpg -O - | sudo apt-key add -
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O - | sudo apt-key add -
``` Download the current release of EasyUbuntu from here

Once downloaded, double-click on the package to install.

---

### Post by Linux&amp;Lizards on 2006-12-17
sry I'm using edgy

---

### Post by aysiu on 2006-12-17
The Edgy instructions are also on the website and very similar: > For Edgy and Dapper Users: New Alpha

This alpha release supports:

    * Ubuntu/Kubuntu/Xubuntu
    * Dapper/Edgy
    * x86/powerpc/amd64


NOTE: After you download EasyUbuntu, PLEASE run the following commands:
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O - | sudo apt-key add -
```

Download the alpha release of EasyUbuntu from [here](http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb)

Once downloaded, double-click on the package to install.

---

### Post by Linux&amp;Lizards on 2006-12-17
this is what I get while trying to install the programs.


[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz:) 404 Not Found

---

### Post by aysiu on 2006-12-17
Okay, what about if we forget the gpg keys for now. Can you paste these commands into the terminal? ```
wget -c http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb
sudo dpkg -i easyubuntu_latest.deb
```

---

### Post by Linux&amp;Lizards on 2006-12-17
those commands had no problems.

---

