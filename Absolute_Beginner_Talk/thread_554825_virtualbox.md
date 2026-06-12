---
title: "virtualbox"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by h0z3r on 2007-09-19
i am trying to use virtual box on fiesty to run XP, i set up an expanding drive starting at 10 gigs, about 300mb ram. when i try to start the machine to install xp i get a warning saying, 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
does anyone know what to do?

---

### Post by Vadi on 2007-09-19
Yeah, you need to make the vboxdrv group and add yourself to it.

Check out this wiki article ([click]("https://help.ubuntu.com/community/VirtualBox?highlight=%28virtualbox%29")) on how.

---

### Post by tgm4883 on 2007-09-19
> **h0z3r said:**
> i am trying to use virtual box on fiesty to run XP, i set up an expanding drive starting at 10 gigs, about 300mb ram. when i try to start the machine to install xp i get a warning saying, 
The VirtualBox kernel driver is not accessible to the current user. **Make sure that the user has write permissions for /dev/vboxdrv _by adding them to the vboxusers groups_**. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
does anyone know what to do?

Yep, that one isn't exactly rocket science.  

If I had to take a stab in the dark, I would guess that you need to add your current user to the group vboxusers, then log out and back in.

Seriously, I know this is the beginners forum, but come on!

---

### Post by h0z3r on 2007-09-19
ya, simple im sure. not so simple when this is your 4th day on linux. lol

---

### Post by h0z3r on 2007-09-19
> **tgm4883 said:**
> Yep, that one isn't exactly rocket science.  

If I had to take a stab in the dark, I would guess that you need to add your current user to the group vboxusers, then log out and back in.

Seriously, I know this is the beginners forum, but come on!

i can understand what it means. what im asking is how.

---

### Post by h0z3r on 2007-09-19
thanks for the link vadi

---

### Post by swisscow on 2007-09-19
Go to system, admin (I think) users and groups. Navigate through to manage groups, fing the vboxusers group, edit it and add your login. I don't know th exact path because I'm using Kubuntu.


Fair question by the way, as it says in the forum rules this group is for anything

---

### Post by mysticmatrix on 2007-09-19
> **h0z3r said:**
> i can understand what it means. what im asking is how.
USe System --> Administration --> Users and Group. Right click on your user name, select properties and add yourself to required group.

---

### Post by h0z3r on 2007-09-19
thanks swisscow and mysticmatrix. i cant wait to see it up and running
thanks again

---

