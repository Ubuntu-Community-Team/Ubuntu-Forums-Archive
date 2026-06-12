---
title: "Manual Removal of KDE desktop"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-04-24
when trying to remove the KDE desktop via the instructions given at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

```
Code:

mjar@mjar:~$ sudo aptitude remove kubuntu-desktop
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
mjar@mjar:~$

```

as output...can you please advise?
:confused:

---

### Post by Seisen on 2007-04-24
Put this in the terminal

```
sudo dpkg --configure -a
```

---

### Post by mkjarema on 2007-04-24
> **Seisen said:**
> Put this in the terminal

```
sudo dpkg --configure -a
```

What does that command do?  It helped a couple situations now.....hmmm

---

