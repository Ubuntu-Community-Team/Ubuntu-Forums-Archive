---
title: "Unable to install &quot;proftpd&quot;"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-03-12
Hi, I am fairly new to Linux and Ubuntu. Every thing i have tryed to do has worked fine but this one thing.

```
sudo apt-get install proftpd
```

I get an error

```
E: Couldn't find package proftpd
```

and i also get the same thing when i try to install "phpmyadmin"

:confused: :confused: :confused: 

Is there something that i am missing? Or is there another way to install a ftp server?

Please help. 

Cheers, 

Loic.

---

### Post by taurus on 2007-03-12
Did you enable both universe and multiverse first?

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all lines that start with **deb**.  Save it and then run

```
sudo aptitude update
sudo aptitude install proftpd gproftpd
```

---

### Post by qpwoeiruty on 2007-03-12
Try going into synaptic and in settings/repositories, check universe and see if you can find it then.

---

### Post by nhandler on 2007-03-12
Try posting the output (if any) from this command:
```
sudo aptitude search proftpd
```

---

### Post by LoicNyssen on 2007-03-12
Thank you taurus, That seems to work now :D

---

