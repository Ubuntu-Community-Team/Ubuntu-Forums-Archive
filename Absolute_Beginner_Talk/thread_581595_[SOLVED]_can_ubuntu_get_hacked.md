---
title: "[SOLVED] can ubuntu get hacked?????????"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by khurrum1990 on 2007-10-19
Hi, can this happen. I just reinstalled Ubuntu 7.10 RC1 to get rid of windows and was downloading upgrades. I just left it for a second noticed Ubuntu automaically switched to second desktop. I switched it back not thinking much about it and while the upgrades were getting installed the show detail options just popped out. wtf?? is this possible or it could be a bug?


Does 7.10 need a firewall or should I reinstall

---

### Post by mlentink on 2007-10-19
Do you have a VNC server installed? Remote Desktop enabled?

---

### Post by milton1 on 2007-10-19
To answer your title, any system can be hacked, if the hacker is good enough. The trick is to avoid making a target of yourself. Ubuntu does a pretty good job of this by default. You have a firewall setup by default (iptables) that can be easily modified with firestarter if you want to allow certain ports. By default,  I believe the only open port is ipp (631).

---

### Post by khurrum1990 on 2007-10-19
Hi, no nothing is enabled, ts a fresh install. It could be a bug maybe because on my previous install sometimes the terminal would disappaear. It just seems weird though.

---

### Post by tkharris on 2007-10-19
milton1: nah-uh.  My system is completely unhackable!

Until I turn it on.  :(

---

### Post by FredB on 2007-10-19
> **tkharris said:**
> milton1: nah-uh.  My system is completely unhackable!

Until I turn it on.  :(

Hacking an unix is harder than a windows. Finding root password is more important than rough attack on an unix.

---

### Post by Frak on 2007-10-19
Ubuntu **can** be hacked. Though it is VERY difficult.
 IP tables is the built in firewall.

click the link below to install the firewall manager: Firestarter
[apt:firestarter]("apt:firestarter")

---

### Post by tkharris on 2007-10-19
> **FredB said:**
> Hacking an unix is harder than a windows. Finding root password is more important than rough attack on an unix.

Finding and cracking a root password is the lamest way of attacking a unix system.  I'd take a remote root exploit over a shadow file any day of the week, or just start reading some of the horribly insecure php code that's so popular today.

---

### Post by mivo on 2007-10-19
It can be easier to "hack" a Linux system if people are careless, i.e. installing servers or running with root privileges, like in Windows. Ubuntu is fairly secure out of the box, so if you don't randomly install anything that you don't fully understand, open certain ports without reading up on possible downsides, etc. you should be fine. What you describe sounds more like a malfunctioning mouse.

---

### Post by khurrum1990 on 2007-10-19
do u think I should reinstall even though everything seems pretty normal now though I will remind u that Iw as using RC1 and it may have some bugs, I just upgraded to the complete version right now

---

### Post by Frak on 2007-10-19
> **mivo said:**
> It can be easier to "hack" a Linux system if people are careless, i.e. installing servers or running with root privileges, like in Windows. Ubuntu is fairly secure out of the box, so if you don't randomly install anything that you don't fully understand, open certain ports without reading up on possible downsides, etc. you should be fine. What you describe sounds more like a malfunctioning mouse.
Good point, the greatest security threat is the PEBKAC

---

### Post by Frak on 2007-10-19
> **khurrum1990 said:**
> do u think I should reinstall even though everything seems pretty normal now though I will remind u that Iw as using RC1 and it may have some bugs, I just upgraded to the complete version right now
You should be fine.

---

### Post by Absorbed on 2007-10-19
If you're a little paranoid, you can install rkhunter. But I imagine you only really need that if you're running a server of some description.

```
sudo apt-get install rkhunter
```

---

### Post by khurrum1990 on 2007-10-19
thanks if I notice anything odd again I will ask u all, till now everything is cool. even my suspend and hibernate works and stuff. continue talking about hacking unix if u like

---

### Post by Frak on 2007-10-19
> **khurrum1990 said:**
> thanks if I notice anything odd again I will ask u all, till now everything is cool. even my suspend and hibernate works and stuff. continue talking about hacking unix if u like
:lolflag:

Also, beware of Social Engineering, it is the greatest hacking device available.

---

