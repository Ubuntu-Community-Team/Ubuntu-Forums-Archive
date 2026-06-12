---
title: "BCM43XX problems on startup"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-11-30
the BCM43XX driver I am using with my HP laptop has been giving me lots of trouble lately.  On startup I always am able to connect to my WPA encrypted wireless internet (through my router).  But sometimes it says I am connected but none of my programs that use the internet work.  They give errors such as "Error:500  cannot find route to the host" or something like that.

I also cannot connect to routers that do not have encryption, or that have WEP encryption.

It would also be nice if I could not have to enter my password every time to unlock the keyring so my computer could wirelessly connect to the internet.

---

### Post by Xbehave on 2007-12-11
my BCM43XX drivers are also abit weird, my workarounds:
i installed ndiswrapper then isntalled propertary drivers (gives me less range but sometimes works when bcm43xx is being wierd
```
sudo modprobe -r bcm43xx ; sudo modprobe bcm43xx
```
Restart driver
```
sudo modprobe -r bcm43xx ; sudo  modprobe ndiswrapper  
```
switch to ndiswrapper
sometimes when trying to connect to a cisco network i need to restart my entire network stuff (not sure if it helps but it seams to)
> sudo killall -9 NetworkManager ; sudo modprobe -r bcm43xx
* im in kde so also quit knetwork manager before starting backup
> sudo NetworkManager ; sudo modprobe bcm43xx
or
> sudo NetworkManager ; sudo modprobe ndiswrapper

even with this i sometimes have to try to re-conenct 3 times before getting a stable connection

---

