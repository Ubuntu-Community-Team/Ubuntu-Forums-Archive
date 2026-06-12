---
title: "Help!"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by kraddark on 2008-02-11
when i start ubuntu i got distoted graphics even on the log-on screen.. i see lines.. how can i solve this?

---

### Post by jan quark on 2008-02-11
what is yur graphic card?

what ubuntu version do you use?

try to login into the failsave gnome session during the login screen

some more info would be nice :)

---

### Post by oedha on 2008-02-11
have you make sure the cable is plug correctly......?

---

### Post by kraddark on 2008-02-11
okay..  my graphics works on winxp.. i have dual-boot... i am using ati x1650pro on ubuntu 7.10 it works well with it... i don't know what i have done but after i restarted the computer.. my graphics on ubuntu were all distored ( sometimes only lines).. and i cant login because i can't see what i need to click.. what should i do?

---

### Post by hyper_ch on 2008-02-11
also make sure next time, that you use a descriptive thread title and not just a generic "need help"

---

### Post by kraddark on 2008-02-11
okay.. my graphics works on winxp.. i have dual-boot... i am using ati x1650pro on ubuntu 7.10 it works well with it... i don't know what i have done but after i restarted the computer.. my graphics on ubuntu were all distored ( sometimes only lines).. and i cant login because i can't see what i need to click.. what should i do?

---

### Post by erginemr on 2008-02-11
Try taking a copy of your current xorg.conf file with:
```
sudo cp /etc/X117xorg.conf /etc/X11/xorg.conf.mybackup
```
and reconfigure your X server:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart your graphical server with Ctrl+Alt+BackSpace to see if it helps.

---

### Post by erginemr on 2008-02-11
If you have installed the binary ATI driver, following this howto:
[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

there should be an ATI specific command too, to configure your graphics card:
```
sudo aticonfig --initial
```

Otherwise, post your xorg.conf file here and we shall try some other tricks.

---

