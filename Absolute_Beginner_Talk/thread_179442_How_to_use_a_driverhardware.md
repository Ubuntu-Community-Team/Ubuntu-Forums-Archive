---
title: "How to use a driver/hardware?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by dontpanic0 on 2006-05-19
I downloaded a driver for my wireless USB adapter.  I copied the files to the correct directory (the readme specified it).  How do I use the driver/hardware for internet access?  
Thanks in advance,
       Dontpanic0

---

### Post by empthollow on 2006-05-20
the first thing you need to do is find out if the system recognizes that the device is there, in gnome go to:

system -> networking

you should see your device in the list, if you do not the proper kernel module/driver needs to be loaded

if the device is there, click on it and then click the properties box on the right.
select a network from the list and enter key and type if necessary.  make sure the configuration is set to "dhcp".  
click OK
click activate on the right

if all goes well you will have an internet connection

---

### Post by jackbijou on 2006-05-20
so what do you do if you don't see your device? i can see eth0, but not ath0. i'll keep searching these forums, but please guide me if you can. THanks.

---

### Post by empthollow on 2006-05-20
if you do not see the device you need to load ( and possibly install) the kernel module.
```
sudo modprobe module_name
```
if you are looking for an atheros driver (i assume this because you mention the ath device) you need the madwifi module.  this is available through synaptic or apt-get. the package name is "linux-restricted-modules-kernel#"  to get your kernel number type 
```
uname -r
```
in a terminal.  OR you can avoid all that and search for madwifi using synaptic in system -> administration -> synaptic package manager

here is a page where you can look up your adapter and find out what chipset it has.  the kernel module needs to match the chipset. [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)
good luck

---

