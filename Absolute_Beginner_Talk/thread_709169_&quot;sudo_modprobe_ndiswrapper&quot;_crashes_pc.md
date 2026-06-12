---
title: "&quot;sudo modprobe ndiswrapper&quot; crashes pc????"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Guitaraholic on 2008-02-27
im having problems with Kevdog wg111t wireless USb install using ndiswrapper

ve followed this guide perfectly now and everytime i type

sudo modprobe ndiswrapper my pc will crash.....

any one seen this error before?

my pc just freezes and i have to reboot therefore making it impossible for me to install my wireless

help appreciated

the forum guide im using is here
[http://ubuntuforums.org/showthread.php?t=519103&highlight=wg111t](http://ubuntuforums.org/showthread.php?t=519103&highlight=wg111t)

---

### Post by tdrusk on 2008-02-27
Try running
```
sudo depmod -ae
```
then run 
```
sudo modprobe ndiswrapper
```

---

### Post by Guitaraholic on 2008-02-27
yea bin doib a sudo depmod -a


ill try doin depmod -ae


thanks

---

### Post by Guitaraholic on 2008-02-28
tried the advice of another user by doing a 

sudo depmod -ae first 


still same problem.....


No1 ?
not an idea what this could be


im really eager to start using linux must help appreciated

---

### Post by tdrusk on 2008-02-28
Where are you installing  ndiswrapper from, a repository or from the site?

---

### Post by Guitaraholic on 2008-02-28
well i downloaded the most recent ndiswraper from sorce

1.52

n extracted it to ndiswrapper in home folder

then runnging the netgear drivers from a driver folder in home too

i linked to the guide in my first post

---

### Post by Guitaraholic on 2008-02-28
any ideas????


really wanna get my ubuntu up n goin so i dont have to use windows anymore!

---

### Post by coolbrook on 2008-02-28
Sounds like a conflict with the driver or it's corrupt.  Which one are you using?  If not already then consider the [Windows 98/ME version of the driver.](http://kbserver.netgear.com/products/WG111T.asp)

**edit**: I also noticed you made another thread and mentioned WG111**T**v2.  What is the exact model number printed on the adapter?  If it is WG111v2 then try the driver which is linked in my signature instead.

---

