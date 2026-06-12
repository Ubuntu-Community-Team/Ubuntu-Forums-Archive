---
title: "Does Ubuntu?........."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by unixdotseth on 2007-04-30
does ubuntu have a built in firewall? and is it on by default?

---

### Post by ZeroWing on 2007-04-30
> **sethjliford said:**
> does ubuntu have a built in firewall? and is it on by default?

 Yep. IPtables. Way better than Windows...s.

 Go to Synaptic and download firestarter if you want a frontend.

---

### Post by zvacet on 2007-04-30
Yes,it is on by default.And like ZeroWing sed firestarter is just GUI for iptables.

---

### Post by Sef on 2007-04-30
It is part of the kernel.  

> Go to Synaptic and download firestarter if you want a frontend.

The easiest way to install firestarter is via Add/Remove (Applications > Add/Remove):

Search Firestarter > click on box next to firestarter > apply > apply > follow directions to finish.

Another way to install firestarter is via the Terminal (Applications > Accessories > Terminal):

```
sudo aptitude update
```

```
sudo aptitude install firestarter
```

---

### Post by eentonig on 2007-04-30
But, on the other end. Why do you need a FW? When installing linux, by default, no serverports are opened. So unless you start a public service like webserver, ssh, ftp, ... to access your pc remotely there's not really a need for a FW.

---

### Post by Nythain on 2007-04-30
hehe... i use firestarter for a quik graphical way to turn my firewall off

---

