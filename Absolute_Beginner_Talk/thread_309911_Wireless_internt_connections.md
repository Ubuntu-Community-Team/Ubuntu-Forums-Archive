---
title: "Wireless internt connections"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-11-30
Hei all.

Got a small problem, after running ubuntu successfully for about a week - and really enjoying it :D my wireless connection doesnt seem  to work. It seems to connect fine - but firefox and any other internet apps wont work. if I log onto windows then the connecyion is fine, so i know its not the router. Also is there a program/utility for searching for available networks? so you can just point and click connect??

Cheers


Jussi

---

### Post by PartisanEntity on 2006-11-30
> **Jussi01 said:**
> Hei all.

 Also is there a program/utility for searching for available networks? so you can just point and click connect??


Network Manager does that quite nicely, I use it for my wpa encrypted home wifi network.

```
sudo apt-get install network-manager-gnome network-manager
```

I followed [these]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") instructions to get my wpa encrypted wifi set up in Dapper.

---

### Post by kilou on 2006-11-30
I also have wireless issue with Edgy. Wired connection is OK, I can connect with wireless, I can ping IP adresses but I cannot ping website by their names. I read somewhere it's a DNS problem. I still couldn't fix it (but didn't play with it too much lately).

---

