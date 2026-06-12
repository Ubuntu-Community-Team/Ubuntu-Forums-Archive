---
title: "Help me ;_;"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Jeppe1 on 2006-06-26
I wanted to have ubuntu on my system, but I (of some wierd action) installede the server version! Now I'm stuck in that server program!!! How can i delete it and instal the dekstop version instead?
Plaese help me :cry:

---

### Post by kaamos on 2006-06-26
Hello!

You could probably use the command "sudo apt-get install ubuntu-desktop" to get you a more user friendly version of ubuntu. This will take quite a lot of time though unless you have a fast internet connection.

---

### Post by Jeppe1 on 2006-06-26
Thank you, something wierd happened... I hope it will turn out good.

---

### Post by Brunellus on 2006-06-26
sudo apt-get install ubuntu-desktop

will get you the ubuntu default.

sudo apt-get install kubuntu-desktop

will get you kubuntu (KDE)

sudo apt-get install xubuntu-desktop

will get you xubuntu (XFCE)

alternatively, if you're using very old hardware, you might want to investigate the other possible ubuntu configurations for superlightweight installations:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by bruce89 on 2006-06-26
[QUOTE=Brunellus]sudo apt-get install ubuntu-desktop

will get you the ubuntu default.

sudo apt-get install kubuntu-desktop

will get you kubuntu (KDE)

sudo apt-get install xubuntu-desktop

will get you xubuntu (XFCE)

alternatively, if you're using very old hardware, you might want to investigate the other possible ubuntu configurations for superlightweight installations:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)[/QUOTE]
Actually, aptitude is now preferred, see [http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)
So the instructions should be:
```
sudo aptitude install ubuntu-desktop
```
will get you the ubuntu default.
```
sudo aptitude install kubuntu-desktop
```
will get you kubuntu (KDE)
```
sudo aptitude install xubuntu-desktop
```
will get you xubuntu (XFCE)

---

### Post by richbarna on 2006-06-26
preceded with a :-

> sudo aptitude update && upgrade

---

