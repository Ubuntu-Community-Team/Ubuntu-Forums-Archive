---
title: "How would i get a xbox 360 controller to work"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by firenoodles on 2007-02-18
I would like to use my xbox 360 controller with zsnes on this ubuntu server box with a xubuntu gui.
What would i have to do to get it working correctly?
Currently it does not work at all.
:confused:

---

### Post by lenwood on 2007-02-18
[http://ubuntuforums.org/showthread.php?t=164040&highlight=xbox+controller](http://ubuntuforums.org/showthread.php?t=164040&highlight=xbox+controller)

---

### Post by firenoodles on 2007-02-18
> **lenwood said:**
> [http://ubuntuforums.org/showthread.php?t=164040&highlight=xbox+controller](http://ubuntuforums.org/showthread.php?t=164040&highlight=xbox+controller)

Tried that i get this error
make: *** /usr/src/linux: No such file or directory.  Stop.
make: *** [all] Error 2
when i get to the make part

---

### Post by po0f on 2007-02-18
firenoodles,

Make sure you have your kernel headers installed.  From a terminal:

```
[FONT="Courier New"]$ sudo apt-get install linux-headers-$(uname -r)[/FONT]
```

Is this on Dapper or Edgy?

---

### Post by firenoodles on 2007-02-18
> **po0f said:**
> firenoodles,

Make sure you have your kernel headers installed.  From a terminal:

```
[FONT="Courier New"]$ sudo apt-get install linux-headers-$(uname -r)[/FONT]
```

Is this on Dapper or Edgy?

dapper and what do you recommend for a sources.list? now im gettting this error 
make: Nothing to be done for `all'. but i did do a apt-get dist-upgrade

---

