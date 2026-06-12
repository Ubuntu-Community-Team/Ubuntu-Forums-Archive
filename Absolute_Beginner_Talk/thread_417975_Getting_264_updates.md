---
title: "Getting 264 updates"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by goatman on 2007-04-22
I just installed version 6.06 LTS (6.10 wouldn't even start up) and it says that I need 264 updates. When I click on the icon, it asks for an administrator password. It didn't ask me to put in one during the install, so I have tride root, and sudo, neither of which has worked. any guidance would help. Also, is there any chance of getting rid of the ugly brown Gnome colors and getting KDE? :KS 

The reason I am trying to install these is that I don't want to wait 2 months for a mailed CD to get started with Ubuntu, and my burner isn't working so good. :mad: 



Thanks

---

### Post by K.Mandla on 2007-04-22
You should have been asked for user ID and password during installation, and the password for that account is the one that gives you access to the administrative tasks.

You can install KDE right away, if you like. Or you could change the colors of Gnome, too. :)

---

### Post by goatman on 2007-04-22
Thanks, I found out by using "man sudo" that the password was the same as the one I gave myself, so I got those updates :D :D Now to get KDE:KS 
I appreciate the help! :guitar:

---

### Post by goatman on 2007-04-22
OOps, I tried to apt-get KDE and it cannot find the packages. Where would I find that? any ideas? Thanks:KS

---

### Post by altaaa on 2007-04-22
try

```
sudo apt-get install kubuntu-desktop
```

---

### Post by bobplano on 2007-04-22
you might want to use sudo aptitude install kubuntu-desktop. it cleans up better if you ever want to uninstall kde

---

### Post by goatman on 2007-04-22
Thanks guys, it's installing as I type ;):) :)

---

