---
title: "Amarok install issue"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-01-30
when i try to install amarok i use this code

apt-get install amarok

but it gives me this error

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

t does it mean and how to i correct cause im new to ubuntu  and i dont know how to install it with the Tar.b2z file yet 

im useing 7.10 gusty

---

### Post by dgray_from_dc on 2008-01-30
Use ```
sudo apt-get install amarok
```

Installing any package requires admin rights.

---

### Post by articwolf939 on 2008-01-30
Thx alot but now when i do it it give me this error

kyle@kyle-laptop:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok
kyle@kyle-laptop:~$

---

### Post by jan quark on 2008-01-30
just a guess

are your software sources enabled?

go to the menu and to the sources window

are all the available sources checked?

if not do so and run

sudo apt-get update
and try to install amarok again

---

### Post by articwolf939 on 2008-01-30
> **jan quark said:**
> just a guess

are your software sources enabled?

go to the menu and to the sources window

are all the available sources checked?

if not do so and run

sudo apt-get update
and try to install amarok again

Thanks you very very much ive tried installing many products but all gave me the same error now its fix thanks alot :)

---

### Post by jan quark on 2008-01-30
hey good to hear :)

can you please mark this thread as solved
you can do so with  the thread tools which are on top

---

### Post by dgray_from_dc on 2008-01-30
Remember to mark this thread as solved.

---

### Post by yizuman on 2008-02-10
I have Amarok version 1.4.7 and I have downloaded a file for version 1.80, how do I install this file to update the player?

Thanks

Yiz

---

