---
title: "Force Ktorrent on eth1"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by nousefreak on 2007-11-29
Hi, 

I was wondering if there is a way to force my ktorrent (or any other program) to use a specific network connection (eth0 or eth1)

Can somebody help me?

---

### Post by scxtt on 2007-11-29
if you're behind a router, forward the bittorrent ports 6881-6889 to the eth1 IP ... don't know what affect that'll have on the upload, but ...

---

### Post by hyper_ch on 2007-11-29
with the next version of ktorrent you should be able to bind it to a specific card.

---

### Post by Znort_Ubern00b on 2007-11-29
> **hyper_ch said:**
> with the next version of ktorrent you should be able to bind it to a specific card.

When will this be coming out???

---

### Post by hyper_ch on 2007-11-29
I think with Hardy and KDE 4

---

### Post by nousefreak on 2007-11-29
> **scxtt said:**
> if you're behind a router, forward the bittorrent ports 6881-6889 to the eth1 IP ... don't know what affect that'll have on the upload, but ...

I suppose it is done with iptabels, but i'm not quite understanding the manual.

can someone post an example?

---

### Post by scxtt on 2007-11-29
do you have a router between your modem and PC?  that would be an easy way to direct the B.T. traffic ...

it also seems that CLI B.T. programs can use a specific eth. device ...
```
bittorrent-curses -h
Usage: bittorrent-curses [OPTIONS] [TORRENTFILE]

--bind <arg>
          ip to bind to locally (defaults to '')
```

---

### Post by nousefreak on 2008-03-13
It seams i don't have "bittorrent-curses" is there a way I can get it, i can't find it with apt-get 

Thanks

---

### Post by scxtt on 2008-03-14
try **sudo aptitude install bittorrent** and see if you have btdownloadcurses afterwards ...

---

### Post by nousefreak on 2008-04-17
Yes i now indeed have "btdownloadcurses", but how do I use this,

I have 2 available networks:
eth0 (
  IP 192.168.1.12
  Ro 192.168.1.1)
wlan (
  IP 192.168.1.12
  Ro 192.168.1.1)

I cannot change the settings of there routers nor my ip because the all have to stay the same,

what is the bind command when i want it on eth0
and will this also have effect on the traffic of my ktorrent

thanks

---

### Post by hyper_ch on 2008-04-18
btw, with rtorrent you can bind it simply to a given interface :)

---

### Post by nousefreak on 2008-04-28
no more probs where upgrading to 8.04 LTS

thanks you all

---

