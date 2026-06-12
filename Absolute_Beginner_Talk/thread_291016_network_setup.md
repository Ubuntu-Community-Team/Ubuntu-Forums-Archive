---
title: "network setup"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-11-01
hi im trying to set up a network between my windows laptop and my dapper 6.06 
desktop and i have got to here and im stumoed .

rex@Linux:~$ cd /etc/networks
bash: cd: /etc/networks: No such file or directory
rex@Linux:~$ cd /etc/network
rex@Linux:/etc/network$ ls
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces
rex@Linux:/etc/network$ sudo gedit interfaces

got to my interface file.


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

so ive got this far dont know what else to do ,i dont have write permission 
in the windows network file.

 /home/rex/Desktop/Screenshot.png (oops failed here should have been a screen shot)


 so if someone could lead me through the rest of the set up i would be gratefull.
                       thanks  :-k

---

### Post by seshomaru samma on 2006-11-02
I'm not sure if this is what you mean but
I share files between a Dapper desktop and an XP laptop like this (both on the same subnet):
I created a shared folder on XP
I clicked on places>network servers in Ubuntu
Network servers showed something called 'windows network' or something similar (I don't have an Ubuntu here , I might be getting the terms wrong)
I clicked on 'windows network' and can see the XP folder.
I instructed Firestarter to allow this connection.
No terminal work involved.
I couldn't get Windows to see Ubuntu though.

hope this helps

---

