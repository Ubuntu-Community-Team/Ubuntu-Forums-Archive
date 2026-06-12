---
title: "how do i upgrade/update my ubuntu?"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-05-26
](*,) ](*,)

---

### Post by mscman on 2006-05-26
Open a terminal and do```
sudo apt-get update
``` then run ```
sudo apt-get upgrade
```

---

### Post by joshrobinson on 2006-05-26
[QUOTE=the_nomad]](*,) ](*,)[/QUOTE]

upgrade from breezy to dapper? or check for updates and install them

to check for updates you can open update manager from system administration, put your password in, click the check button and if it finds anything click install

to do it from command line aka terminal

sudo apt-get update
sudo apt-get upgrade

to upgrade from breezy to dapper, you are better off downloading a cdimage and doing a fresh install, just make sure you have your personal files backed up

---

### Post by cstudent on 2006-05-26
[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

This might be a good place to start.


.

---

### Post by the_nomad on 2006-05-26
thnx!:cool:

---

### Post by bruce89 on 2006-05-26
If you want to upgrade from breezy to dapper do this : 
```
gksu "update-manager -d"
```
Warning - make a backup of any data on your Ubuntu partition.
Or you can wait until next Thursday, when update-manager will get an extra button on it.

---

