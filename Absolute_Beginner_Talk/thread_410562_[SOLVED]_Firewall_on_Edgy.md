---
title: "[SOLVED] Firewall on Edgy"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-04-15
I am looking for a firewall for my Edgy box.  What is recommended.

Thanks

---

### Post by Seisen on 2007-04-15
You can use Firestarter, which a frontend for IP Tables.

```
sudo aptitude install firestarter
```

---

### Post by speeves on 2007-04-15
I can recommend shorewall, (which is also a front-end for IP Tables), if your box is not mobile.  (ie a server or desktop machine).

---

### Post by pjones0404 on 2007-04-15
ubuntu comes w/ a firewall built in, iptables. 

Firestarter is a front end for it. you do not have to instal a seperate firewall.

---

### Post by Seisen on 2007-04-15
Shorewall is very hard for  a new person to use, thats why I recommended using Firestarter.

---

