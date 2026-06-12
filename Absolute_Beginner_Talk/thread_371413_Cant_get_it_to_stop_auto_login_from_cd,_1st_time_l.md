---
title: "Cant get it to stop auto login from cd, 1st time linux user"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by jzh797s on 2007-02-26
I have tried using Ubuntu, XUbuntu, and all other variants and I get the same thing every time. It will go to the login screen (I have never had an option to set one up), auto login (after 10 seconds), give me a glimps of the main screen (I can even see and click on the icons at the top), and then it auto logs out and starts all over again. 

Can anyone help? Please?

Thanks

---

### Post by shareMenaPeace on 2007-02-26
Maybe it is because your HD space is low?

From login press

STRG + ALT + F2 to access the console - login here and type 

```
df 
```

to see your disk space. 

STRG + ALT + F7 brings you back to the xserver (login).

---

### Post by jzh797s on 2007-02-27
I am running this on an old PC, but the disk is empty and at 12gb.

---

### Post by oldsparks on 2007-02-27
I had this problem in installing Xubuntu too, and think that it was due to only having 160Mb RAM. 
Although Xubuntu will run in 128Mb RAM, the recommended minimum for installation is 192Mb
I eventually managed to overcome the problem by reinstalling using the option for Safe Mode. 
Xubuntu now runs fine on my old 750MHz Duron in 160Mb RAM.

---

### Post by jzh797s on 2007-02-27
I am installing it on an old 500mhz pc with 128 RAM. Maybe the ram is my problem.

---

