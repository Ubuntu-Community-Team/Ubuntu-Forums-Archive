---
title: "missing root data ???"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-05-28
sorry to be dumb - but i just installed ubuntu - when it loads it asks me for my login and password.. and after entering them logs me in a user x...  - am i missing something - at what point did i give it the details of the root login ?? how do i login as root ???? can recall it ever asking me a root used name and password...  tried root - doesnt work ?????

---

### Post by Happy_Man on 2007-05-28
Ubuntu locks root by default. Use sudo and your password to do root stuff.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security) for more info.

---

### Post by taurus on 2007-05-28
You don't log in as root since the root account is locked.  Whatever you need to access something as root, use either sudo or gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lupgop on 2007-05-28
sorry can i get an example ??
lets say my password is "access"
and i want to mount a cdrom drive ?

---

### Post by Happy_Man on 2007-05-28
The terminal code will look like this:
```
lupgop@lupgop:~$sudo mount /dev/cdrom0 /media/CD
Password:
lupgop@lupgop:~$
```

---

### Post by lupgop on 2007-05-28
thanks -- going have to get some new books - any recommendations ??

when i do this it says     /media/CD does not exist

---

### Post by steve.horsley on 2007-05-28
Try mounting it to /media/cdrom:
sudo mount /dev/cdrom0 /media/cdrom

But if you are logged in when you insert the CD, it shouuld automount and appear as an icon on your desktop.

---

### Post by Happy_Man on 2007-05-28
> **lupgop said:**
> thanks -- going have to get some new books - any recommendations ??

when i do this it says     /media/CD does not exist

It was an example; It's not supposed to work. :D

---

