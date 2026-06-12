---
title: "E16 instead of E17?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by SAMW on 2007-05-31
Hello all,

I've recently tried to install e17 on my new computer. I have had exeperience before and like it's shinyness. I followed this link:

[http://ubuntuforums.org/showthread.php?t=319336&highlight=installing+enlightenment+e17](http://ubuntuforums.org/showthread.php?t=319336&highlight=installing+enlightenment+e17)

in another thread to a tutorial on the install. I folllowed all the instructions and selected this repo:

## E17 repository "edevelop.org"
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

After the install however. I realized that I had downloaded e16 instead of 17. Can anyone help me remove e16 and install e17. I've had experience with 16, but hate the way it looks.

---

### Post by hanzomon4 on 2007-06-01
Try ```
sudo apt-get remove enlightenment
```

For e17 I think with the repos you just do this```
sudo apt-get install e17
```

---

### Post by darkmaster on 2007-08-19
Hello, I have this problem too. I used this repos:

## E17 repository "edevelop.org"
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

then I updated and sudo apt-get install e17 but... well... when I restarted gdm there was an enlihtenment entry but when I logged in, it was e16!!! Please, help, I used to have e17 on my old PC, cannot figure out why installing e 17 gives me an install of e16, this is crazy! In this website:

[http://polishlinux.org/apps/window-managers/e17-desktop-enlightenment/](http://polishlinux.org/apps/window-managers/e17-desktop-enlightenment/)

I found interesting information:

-----------------
It may happen that DR16 version of Enlightenment is available in the repositories. In such case it is necessary to force the dependency from 0.16.999.xxx.
To do this, enter the following lines in file /etc/apt/preferences

Package: enlightenment
Pin: version 0.16.999.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999.*
Pin-Priority: 999

Of course, if you prefer graphical way of installing software, you can use Synaptic Package Manager and perform all these actions in the GUI environment.
-----------------

Well, I did it but when I try to install e17 at this point I get this error:

I seguenti pacchetti hanno dipendenze non soddisfatte:
  e17: Dipende: enlightenment (>= 0.16.999) ma non è installabile
       Dipende: emodules-all (>= 0.16.999) ma non sta per essere installato
E: Pacchetto non integro

That sounds like it cannot be installed cause it depends on on >= 0.16 etcetera... well, that's right! Why isn't those packages available? Please, help me. I need it badly :(

---

### Post by darkmaster on 2007-08-19
sorry I made an error here. Substitute edgy with feisty, I run Feisty fawn. In my synaptic I already changed edgy to feisty of course, that'snot the problem...

---

