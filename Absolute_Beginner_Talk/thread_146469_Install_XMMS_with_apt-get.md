---
title: "Install XMMS with apt-get"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Roxxor on 2006-03-18
I want to install XMMS, but I cant with the command ```
sudo apt-get install xmms
```

It says the package is available from other sources. How do I install it with apt-get?

---

### Post by Xian on 2006-03-18
Post the entire output from the terminal.
Also, post what you get with the command below:

$ sudo apt-cache policy xmms

---

### Post by malavar on 2006-03-18
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
read that, i hope it helps. if not paste the exact message for someone else to help you. good luck

---

### Post by Roxxor on 2006-03-18
[QUOTE=Xian]Post the entire output from the terminal.
Also, post what you get with the command below:

$ sudo apt-cache policy xmms[/QUOTE]
I don´t know what that means, but I got 
```
roxxor@laptop:~$ sudo apt-cache policy xmms
sudo: timestamp too far in the future: Mar 18 18:43:17 2006
```

---

### Post by Xian on 2006-03-18
[QUOTE=Roxxor]I don´t know what that means, but I got 
```
roxxor@laptop:~$ sudo apt-cache policy xmms
sudo: timestamp too far in the future: Mar 18 18:43:17 2006
```[/QUOTE]

Uh-oh. I've seen that before and you can read this [BUG](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=285053) for more info.

---

### Post by klahjn on 2006-03-18
ouch....personally in that circumstance, if you are looking to get xmms, then i would grab the source and compile it. at least that way you are getting xmms installed for the meantime.  then come back and mess with the utime and all that other stuff to get apt-get working properly

---

### Post by Roxxor on 2006-03-18
Ok. I will try to compile it myself. 

I just tried to install AMSN with apt-get, but i got this (translated from Swedish): 
```

Following packages have dependencies that couldn't be installed.
amsn: Dependence: imlibl but it can not be installed
           Dependence: sox but it won't be installed
           Dependence: libpng10-0  but it can not be installed
E: Damage packages. 
```

Why can't I install amsn?

---

