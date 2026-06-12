---
title: "add remove and software properties disappear"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by millatoe on 2007-02-11
ok..i've finally got ubuntu up and just managed to stop patting myself on the back, 
but a couple of things arent working, add remove applications and software properties , the add/remove application will load then just dissapear and the software properties will do the same as soon as i enter my password,

ps; I'am not computer savy and have only been using linux for about an hour

---

### Post by taurus on 2007-02-11
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by millatoe on 2007-02-11
thanks for the quick reply tuarus!

alex@alex-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
Reading package lists... Done
alex@alex-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
alex@alex-desktop:~$


but where do i get ob of archives?...should this be a new thread?

---

### Post by taurus on 2007-02-11
I am not exactly sure about your last question but looks like your system is up-to-date.

---

