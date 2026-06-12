---
title: "startx not working"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by tacogrande on 2007-05-28
Just installed a fresh copy of the new server ubuntu.  I tried installing it twice seeing if it just missed installing some of the programs.  But when i load it up i get to the prompt and hit startx it says its not installed and tells me how so i try to do what it says then it locates x11-common and to install that instead so i do and startx still isnt working.  Whats up what did i do wrong?  i thought gnome was supposed to be with this.  anyways let me know what i should do.  thankyou ^_^

---

### Post by meng on 2007-05-28
A server does not have a graphical environment installed by default (that's why startx doesn't work, there's no X-environment installed). Did you really want to install a server, or a desktop? What are you using this computer for.

---

### Post by taurus on 2007-05-28
Server only comes with a command so if you want to run a window manager like Gnome, you need to install it.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

Otherwise, install the desktop CD/LiveCD version.

---

### Post by tacogrande on 2007-05-28
wow that was so fast, i was starting to think that it didnt come with one.  I want to run a server for php and http with ftp server, but with a gui, so i guess i will install the gnome to it manually.  thanks for the responses.

---

### Post by DJ Wings on 2007-05-28
Umm... GDM comes with Ubuntu-Desktop, so you don't need it installed separately...

---

