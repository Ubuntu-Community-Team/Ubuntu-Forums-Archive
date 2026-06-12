---
title: "Wifi - wep + dhcp doesn't work"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-09-27
I just registered at school to have free wifi, and they use 64-bit WEP key I am able to list the network with iwlist scan, then I use ```
iwconfig eth1 essid myssid
```, but ```
dhclient eth1
``` is unable to get an ip.
I tried it on windows and it works.. is there something I can do about it?

my wifi chipset is broadcom 4300

---

### Post by Austin_KW on 2007-09-27
```
sudo iwconfig eth1 key *yourKey*
```
between the 2 commands

---

### Post by kane77 on 2007-09-27
err.. I did (I used the gui network configuration...)

---

### Post by gigaferz on 2007-09-27
imho, do not rely too much on the gui apps...for some x#$%@ reason they might not work sometimes...

do it with the command line

fer@fer-desktop:~$ sudo iwconfig wlan0 essid ferby key open s:3zferby mode Managed   <-- this is an example of  the command i use it to make it work everytime... sometimes i enter it up to five times to get the internet to work...
(is just pressing up and enter,but its annoying sometimes..)

---

### Post by kane77 on 2007-09-27
okay, I will try it with console, but only on monday - we have day off tomorow...

---

