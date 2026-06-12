---
title: "i cannot edit my sources.list"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by StevenEpic on 2007-08-16
i am trying to edit my sources.list so i can install compiz fusion, and i believe editing the sources list is needed. i try to edit the sources list, but it says i don not have permisson. on the terminal i try using this command ```
kdesu kwrite /etc/apt/sources.list
``` then it tells me kdesu is not install. it gives me a command of how to download kdesu or kwrite or whatever, and it asks for a password. i know my passwords, but when i try to type them, nothing happens.

:?

---

### Post by heimo on 2007-08-16
Try gksudo instead of kdesu (just a guess, you might not have that installed), or run 
```
sudo -s
```
and then
```
kwrite /etc/apt/sources.list
```
or what ever editor you have installed (gedit in Gnome)

---

### Post by wolfen69 on 2007-08-16
```
sudo -s -H
``` will make you root. then try to edit.```
sudo nano /etc/apt/sources.list
```

---

### Post by mikewhatever on 2007-08-16
If you are Ubuntu 7.04 Feisty Fawn User, there is no wonder kdesu is not installed.
Use gksudo gedit /... instead. When you type the password, nothing shows, so that's normal.

---

### Post by StevenEpic on 2007-08-16
ok how exactly can i edit the file. [i have this]("http://i13.tinypic.com/4l90bgn.png"), and i wanna save the file in order to install compiz. please forgive my ignorance.

---

### Post by overdrank on 2007-08-16
> **StevenEpic said:**
> ok how exactly can i edit the file. [i have this]("http://i13.tinypic.com/4l90bgn.png"), and i wanna save the file in order to install compiz. please forgive my ignorance.

Just add the additional repos and save it. Then run sudo apt-get update or aptitude instead of apt-get and should be good to go!

Edit: HymnToLife is correct.

---

### Post by Bachstelze on 2007-08-16
Close Gedit and type this in your terminal

```
gksudo gedit /etc/apt/sources.list
```

That's all.

---

### Post by StevenEpic on 2007-08-16
omg that simple? thank you so much :D

---

