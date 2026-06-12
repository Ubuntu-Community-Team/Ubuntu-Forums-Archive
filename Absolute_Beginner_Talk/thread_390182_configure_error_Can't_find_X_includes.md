---
title: "configure: error: Can't find X includes"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-03-21
Hi
I am trying to install a bit of software called qsstv-5.3c I have unpacked it and gone to the directory in terminal where it is located, then as the installation say I type ./configure, all is fine then i get this error message:-

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

What does it mean???

thanks
Ian

---

### Post by Bachstelze on 2007-03-21
Do :

```
sudo apt-get install xorg-dev
```

then try configuring your software again.

Good luck :)

---

### Post by ianb72 on 2007-03-21
> **HymnToLife said:**
> Do :

```
sudo apt-get install xorg-dev
```

then try configuring your software again.

Good luck :)
Thanks
I'm trying it now :-)

---

### Post by ianb72 on 2007-03-21
Right that worked great, now I am getting this error when I type ./configure:-

checking for Qt... configure: error: Qt (>= Qt 3.1.0) (headers and libraries) not found. Please check your installation!

Any ideas again?

Forgive me for being stupid but I've been a slave to windoze and now want something better.

Ian

---

### Post by Bachstelze on 2007-03-21
```
sudo apt-get install libqt3-mt-dev
```

---

### Post by ianb72 on 2007-03-21
> **HymnToLife said:**
> ```
sudo apt-get install libqt3-mt-dev
```
How do you learn about all of this stuff and the commands for it all, as I would love to start learning myself instead of making an idoit of myself on here!! lol

Ian

---

### Post by Bachstelze on 2007-03-21
You need stuff regarding X. Since Ubuntu uses Xorg, the package will most likely have xorg in it's name. But you don't need Xorg itself - you already have it - but all the headers, includes and other developpement files. Developpement files for Xorg = xorg-dev :)

Basically, when you're told you need the headers/includes for something, just search for it in Synaptic and look for packges ending with -dev.

---

