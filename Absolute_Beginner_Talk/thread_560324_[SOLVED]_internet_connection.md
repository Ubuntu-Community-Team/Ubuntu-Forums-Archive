---
title: "[SOLVED] internet connection"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by matchstich on 2007-09-26
hi ,

  have been searching the forums for a couple of days

compaq deskpro en    -installed   feisty


my cable would not plug in the  connection on the box, so i put in 

another card and it will plug in to that one.

when i hover over the network icon, it say i am connected.

but all i get is  sever can not be found.

i tried different things i found on here but nothing seems to work.

i even put in all the info as my network connection shows on this machine

like ip and domain name.  both this machine and the deskpro are set for automatic

but, no joy.

any ideas?

thanks

it is probably something really simple.

---

### Post by RaZer0r on 2007-09-26
could you post the output of: 
```

ifconfig

```

---

### Post by matchstich on 2007-09-26
ok, but this going to be a lot of typing, that computer on other side of the room. lol

eth0    link encap:ethernet  hwadder 00:02:A5:84:3D:79
up bradcast multicast  wtu:1500  metric:1
rx packets:0  errors:0  dropped:0  over runs:0  frmaes:0
tx packets:0  errors:0  dropped: 0  over runs: 0 carrier:0  clollisions:0
 tx queue:1000  rx bytes :0 (0.0b)  tx bytes:0 (0.0b)


eth2  link encap: ethernt hwadder FF.FF.FF.FF.FF
inet6 addr:Fe88:FdFF: FFFF.FEFF.FFFF/64
scope: link up bradcast running milti cast  mtu:1500  metric 1
rx packets : 0  errors:0  dropped: 2494967251
over runs: 0 frmaes:0
collisions:0  txqueuelen: 1000
rx bytes:0 (0.0b) tx bytes:0  (0.0b)
interupt:19 base address:0xa000

eth 0:  avah link encap: ethernet hwadder 00.0.:a5.84.3d.79
inet addr: 169.254.254.6.42
bcast: 169.254.255.255  mask:255.255.0.0
up bradcast multicast  mtu:1500 metric:1

eth2:  avah link encap: ethernet hwadder 00.02.a5.84.3d.79
inet addr: 169.254.6.42 bcast 169.254.255.255 mask:255.255.0.0
up bradcast running multicastt  mtu:1500  metric:1

lo   link encap: local loopback
inet addr: 127.0.0.1  mask:255.0.0.0
up loop back running  mtu:16436 metric:1
rx packets:102  errors:0  dropped:0
overruns:0  frame:0
tx packets:102 errors:0 dropped:0 overruns:0  carrier:0
collisions:0  txqueuelen:0
rx bytes:9072 (8.8 kib)  tx bytes: 9072 (8.8 kib



hope it is right.

thanks

---

### Post by matchstich on 2007-09-26
i tried to edit and correct some mistakes but the forum won't let me

i put bradcast meant to say broadcast

thanks

---

### Post by matchstich on 2007-09-28
i am now on the net.

installed 7.04  and that would not work.

installed  kunbuntu 6.06  ----would not work 

put ubuntu 6.06 lts on it and it works.


i am  ok with that.  don't know why .


thanks yall

---

