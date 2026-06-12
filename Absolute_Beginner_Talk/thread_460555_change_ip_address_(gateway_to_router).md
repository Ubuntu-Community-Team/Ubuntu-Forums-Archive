---
title: "change ip address (gateway to router)"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by dabaconboy on 2007-05-31
I have just installed ubuntu 6.06.1 and i have had a few probs getting on the net. 

now on the connection settings i have on ubuntu are that it is trying to find my belkin router on 127.0.0.1 however the router is set to 192.168.2.1 and cannot be changed to meet the needs of ubuntu. 

when i go to change the settings i have a loopback adaptor dropdown thingy with no other options and then a "grayed out" button that i assume all the settings are behind. 

is there a way to change it to 192.168.2.1 or am i gonna have to stick with windoze. :)

appreciate any help

Dab

---

### Post by daimaru on 2007-05-31
since you only have the loopback device listed maybe your ethernet card wasnt even recognised (or ur wireless?)
but to add a default route go to applications-->accessories-->terminal
edit: first check if your network device is at all listed
```
ifconfig
```
or for wireless
```
iwconfig
```
you should have eth1 eth0 or something in there if it only shows lo then your networkcard is not there

to check your current route type
```
route
```
to change the default gateway type
```
route -add default gw 192.168.2.1
```

if you get an error you might have to 
sudo route -add ...

---

