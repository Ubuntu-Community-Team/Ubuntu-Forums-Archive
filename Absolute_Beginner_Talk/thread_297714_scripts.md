---
title: "scripts"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by kornoholio on 2006-11-11
how can i make a script to run @ startup 
like lets say change my mac address without going through the ifconfig process

---

### Post by loclei on 2006-11-11
sudo gedit /etc/network/interfaces 
and add the hwaddr ether XX:XX:XX:XX:XX:XX
to the interface you want the mac to be changed

---

### Post by kornoholio on 2006-11-11
okey , this is the output of the file 

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


my interface is "eth0" .. cant seem to find it

---

### Post by loclei on 2006-11-11
you should use system > administration > networking and change the status of 
eth0 to static, then modify the ip that you want and after that use the command i wrote earlier

---

