---
title: "URGENT: How can I install X from the ISO?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Carlos Santiago on 2007-03-02
Hi.
Due to some strange problem ([http://ubuntuforums.org/showthread.php?p=2235546)](http://ubuntuforums.org/showthread.php?p=2235546)), my system lost the X Window.
Moreover, my CD-ROM is broke!

I got console with Internet. Only X Window and all applications with GUI are missing. 
Startx shows a gray desktop with a small unmovable console, and the mouse is a gray X. 

Thats definitively not the X window I want!!!

I can install X either from net, or from the Ubuntu ISO. However I dont know how. Can anyone plz help? This is very urgent.

Thank you in advance

---

### Post by taurus on 2007-03-02
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by Carlos Santiago on 2007-03-02
Taurus, thanx for you answer.
Will the comand 'sudo aptitude install ubuntu-desktop' it install all default packages?
like openoffice, firefox, etc, etc

---

### Post by Xappe on 2007-03-02
> **Carlos Santiago said:**
> Taurus, thanx for you answer.
Will the comand 'sudo aptitude install ubuntu-desktop' it install all default packages?
like openoffice, firefox, etc, etc

yes

---

### Post by az on 2007-03-02
Depending on what caused the problem, you may want to run

sudo apt-get -f install

to fix half-installed packages...

---

