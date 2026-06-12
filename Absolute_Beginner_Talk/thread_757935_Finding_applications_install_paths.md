---
title: "Finding applications install paths"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by rocker9455 on 2008-04-17
hi just wondering how i can find out where a program is installed (e.g what directory etc)

---

### Post by MightyMag on 2008-04-17
9 times out 10 it's installed in /usr/bin.

---

### Post by oldos2er on 2008-04-17
In a terminal, run "sudo updatedb", then "whereis <program name>"

---

### Post by forrestcupp on 2008-04-17
Or if you installed it with apt-get or Synaptic, find the package in Synaptic, press the 'Properties' button and click the 'Installed Files' tab to see all of the directories that package installed to.

But it is correct that a lot of times, the binary file is installed to /usr/bin or if it's a game, maybe /usr/games.

---

### Post by tnl2k7 on 2008-04-17
Hello,

If you install an application from an installer that's not a .deb package (the type that Ubuntu usually uses for installers), it might be in '/opt/'.

---

### Post by rocker9455 on 2008-04-17
thanks everyone :D thats alot of help

---

### Post by Oldsoldier2003 on 2008-04-17
> **rocker9455 said:**
> thanks everyone :D thats alot of help

grins theyre a helpful lot the UCF folks. I'm surprised nobody told you 
```
which firefox
``` for example... Just goes to show you how many ways there are to skin a cat in Ubuntu and GNU/Linux

---

