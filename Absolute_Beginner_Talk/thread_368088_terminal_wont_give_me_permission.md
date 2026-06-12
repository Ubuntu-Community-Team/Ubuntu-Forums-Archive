---
title: "terminal wont give me permission"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by windfer on 2007-02-22
alright some how i got ubuntu installed. everything is going great except terminal isn't giving me permission for apt-get it says

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


when i type yes it just says


y
y
y
y
y
y
what do i do

thank you in advance for your help and kindness

---

### Post by Maestro23 on 2007-02-22
If you have Synaptic or add/remove opened, close them.  Then run your sudo apt-get.

---

### Post by taurus on 2007-02-22
```
sudo aptitude update
sudo aptitude upgrade
```
You need to use sudo.

---

### Post by teaker1s on 2007-02-22
we use sudo to gain temp root access
eg
```
sudo apt-get install ubuntu-desktop
```

for graphical programs we use gksudo
eg
```
gksudo synaptic
```

I guess you know linux but not debian/ubuntu?

to be root

```
sudo su
```

---

### Post by geezerone on 2007-02-22
sudo before commands gives you 'admin' rights to change files which you otherwise wouldn't be able to and password lasts for about 15mins. After this you would need to re-enter the / password.

---

### Post by luke411 on 2007-02-22
If you just installed the OS, you need to change the root password. Go to System - Administration - Users and Groups. There, double-click on "root" and change the password boxes to something you will remember. This will be the password you need when you type "su" in the terminal or "sudo". Then try your commands once you entered the password.

---

