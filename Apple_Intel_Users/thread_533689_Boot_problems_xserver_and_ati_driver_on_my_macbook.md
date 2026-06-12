---
title: "Boot problems xserver and ati driver on my macbook pro"
date: 2007-08-24
forum: Apple Intel Users
---

### Post by Emac on 2007-08-24
I have a Macbook Pro computer with:

Intel Core Duo 2,33GHz 
x1600 Ati 
2GB ram 
120GB HD

My problem with installing Ubuntu Linux is that the drivers on ubuntu live cd is filthy.
What I did was went into terminal window and wrote

sudo apt-get update
sudo apt-get instal xorg-driver-fglrx
sudo startx

Then i manage to install ubuntu.
Every time when i boot up, it seems to go well but when it is ready to start up xserver and run ati drivers it comes up a screen it failed under boot. What ideas can u give me to install ati drivers on my hdd and get rid of this problem?

---

### Post by cyberdork33 on 2007-08-24
Use Alt+F1 to get to a terminal. Login and do:
```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```

---

