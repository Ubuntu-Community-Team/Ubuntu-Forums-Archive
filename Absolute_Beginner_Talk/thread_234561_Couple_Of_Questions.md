---
title: "Couple Of Questions"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by tc3racer on 2006-08-11
Im am thinking of building a web server using linux ubuntu server 6 would be a good idea to install a firewall and antivirus or not

---

### Post by 23meg on 2006-08-11
It would be a good idea to install both. A firewall of some sort is a must have on a server, and an antivirus app would help possible viruses for other platforms (they're not a real threat to Linux) ending up on your server from spreading.

---

### Post by powder on 2006-08-11
You probably shouldn't be running a server if you have to ask this, but you will definitely need to set up a firewall.  I would only use an A/V if hosting any windows files.

---

### Post by msak007 on 2006-08-11
That was only 1 question :). But to answer it, yes it's always a good idea to install a firewall / antivirus regardless of the OS you're running. We don't want to start being smug like Mac OS users who think they're immune to all that stuff ;). Ubuntu, and Linux in general, has a firewall installed by default called "iptables". You can install a GUI interface such as FireStarter, GuardDog, or KMyFirewall to configure it if you don't know the syntax. There's no default anti-virus so you can install any of several different apps like clamav, fprot, or AVG.

EDIT: Sorry I answered before fully comprehending the question - if you're only going to be installing a base server and no X window manager, then you don't want to install any of the GUI front-ends because, duh, they require a graphical window manager. You can still get by with iptables, and f-prot or clamav for anti-virus.

---

### Post by powder on 2006-08-11
Installing gui-based apps like firestarter is probably not the best solution. ;)  He should be able to find some good tutorials on how to configure iptables manually.

Edit: Sorry, didn't see your edit. :)

---

### Post by msak007 on 2006-08-11
Haha no prob - I always answer too fast before fully thinking something through.

---

