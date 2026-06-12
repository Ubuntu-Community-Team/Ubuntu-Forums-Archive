---
title: "Firewall?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by zeroo on 2007-03-25
How do you open ports with the built in firewall?

---

### Post by dpar on 2007-03-25
Use Firestarter. It's in the repositories.

---

### Post by stokedfish on 2007-03-25
A firewall is not needed for an Ubuntu desktop system.

---

### Post by zeroo on 2007-03-25
How do you get to firestarter?

---

### Post by ThrobbingBrain66 on 2007-03-25
> **zeroo said:**
> How do you get to firestarter?

System > Admin > Synatpic

search for firestarter and install it.

After that it can be located in System > Admin > Firestarter

From there you can open ports, etc.

---

### Post by ThrobbingBrain66 on 2007-03-25
> **stokedfish said:**
> A firewall is not needed for an Ubuntu desktop system.

Certainly an arguement can be made either way.  iptables is installed by default, whether one chooses to use it or not is up to the user.  Firestarter is merely a GUI for configuring iptables.  Besides that, the OP never mentioned what he/she wanted the firewall for and could very well be using it something more than just a desktop.

---

### Post by zeroo on 2007-03-25
When I go to system I have nothing that says admin.

---

### Post by cobray on 2007-03-25
Try "System -> Administration" :roll:

---

### Post by zeroo on 2007-03-25
I've got nothing under admin or administrator.

---

### Post by ThrobbingBrain66 on 2007-03-25
That's odd.  Well, open a terminal (Applications > Accessories > Terminal) and type
```
sudo apt-get install firestarter
```
then after firestarter is installed type
```
gksu firestarter
```
and you'll be able to configure your firewall.

---

