---
title: "request new IP from ISP.(adsl internet)"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by medya on 2007-08-10
hey in windows they get a new ip from ISP by these commands


ipconfig /flushdns
ipconfig /release
ipconfig /renew
exit


what are the equvalent commands in linux ?

---

### Post by SOULRiDER on 2007-08-10
I dont know how you can do it, you can however unplug and plug in your modem, that sould request a new IP.

---

### Post by renzokuken on 2007-08-10
sudo ifdown eth0

then

sudo ifup eth0

possibly?????

but that only works if your ip is assigned driectly by your ISP and not by a router or something

---

### Post by aitorcalero on 2007-08-10
I think the best way to renew your IP address is to switch off your modem / cable modem. Start it again, and then you can choose betwen two options:
1.- Deactivate / Activate network through networkManager icon (usually top right) or,
2.- In a terminal:
```
sudo /etc/init.d/networking restart
```
an forget about get messy with ethXXX... ;)

---

### Post by bjarneh on 2007-08-10
if you use the network manager i think restarting the network and so on using the command-line can cause some problems, network manager should also be restarted at least if one does that, atleast i think i had some problems with that at some point...

---

