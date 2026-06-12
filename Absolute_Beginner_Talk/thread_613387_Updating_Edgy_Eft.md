---
title: "Updating Edgy Eft ??"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by zipped on 2007-11-14
Hola, i'm very new Ubuntu user, currently i already installed 6.10 (Edgy Eft), please give me instruction to upgrade this edgy into the latest version, thank you. :KS

---

### Post by lordpuppet on 2007-11-14
It's simple:
First

```
sudo apt-get update

```

Then, a dist-upgrade:

```
sudo apt-get dist-upgrade
```

When finish, replace "feisty" with "gutsy" in your sources list:

```
sudo gedit /etc/apt/sources.list
```

Then, again:


```
sudo apt-get update

```
```
sudo apt-get dist-upgrade
```

---

### Post by zipped on 2007-11-15
What size of uprgrade file ?? 
And if i updated my edgy, do GNOME get updated too ??

---

### Post by Inxsible on 2007-11-15
I don't think you can easily upgrade from edgy to gutsy. I would recommend doing a clean install of Gutsy. It will save you a lot of grief.

you can simply install in the same partition where you have your edgy. If you have a separate home partition, then all your settings will be saved too.

or if you like, and if you have spare space, you can install Gutsy in a separate partition, configure it to the way you want and then maybe delete edgy later, if required. That way, even if something goes wrong with the Gutsy install, you can still fall back on your edgy install.

hope that helps.

---

