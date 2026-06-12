---
title: "Do i really need a firewall?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-16
Well i installed firestarter, but is it really necessary? Some people say it's not, some say it is.

---

### Post by arpunk on 2005-12-16
[QUOTE=Rackerz]Well i installed firestarter, but is it really necessary? Some people say it's not, some say it is.[/QUOTE]
Depends of your needs and what services you want to run, etc...

---

### Post by trivialpackets on 2005-12-16
Need is very subjective.  Is it a good idea?  Most of the time I would say yes.

---

### Post by J_P on 2005-12-16
I use firestarter too and and get hits on it 6 serious ones at the moment should this not be happening?

---

### Post by arpunk on 2005-12-16
[QUOTE=eric.proctor]Need is very subjective.  Is it a good idea?  Most of the time I would say yes.[/QUOTE]
It really depends of the services you running, a firewall can be a pain if you running a desktop box, mostly because desktop users uses p2p and other kind of services, but in a server enviroment, things are pretty different.

---

### Post by earobinson on 2005-12-16
everyone will have a diferent answer for this. search the forums many people have had huge debates over linux security

FACT: I have no firewall AV spyware dector or anything else and I have never had a problem

---

### Post by linbetwin on 2005-12-16
Firestarter is a frontend for the firewall, not a firewall in itself.

---

### Post by kaamos on 2005-12-16
Either way, it should be noted that ubuntu has no open ports by default.

---

### Post by psusi on 2005-12-16
For an out of the box default ubuntu install?  No, you won't have any services listening on the network for people to connect to.  

If you start installing things like a samba server, then you might want a firewall.  Usually though, the reason you install samba is to share files with other computers on the network, and the network is going through a router to get to the Internet, and the router provides the firewall.

---

### Post by Mustard on 2005-12-16
[QUOTE=Rackerz]Well i installed firestarter, but is it really necessary? Some people say it's not, some say it is.[/QUOTE]

Some people, like me, just like to know what is going on in terms of active connections and hits on the firewall.  It's a comfort thing, like a security blanket. ;)

---

### Post by psusi on 2005-12-16
For that kind of thing, I find things like ethereal to be much more interesting ;)

There was a nifty command line utility that tracked the tcp and udp conversations going on, and was simpler than ethereal, but I can't remember the name of the darned thing now...

[QUOTE=Mustard]Some people, like me, just like to know what is going on in terms of active connections and hits on the firewall.  It's a comfort thing, like a security blanket. ;)[/QUOTE]

---

### Post by Mustard on 2005-12-16
[QUOTE=psusi]For that kind of thing, I find things like ethereal to be much more interesting ;)

There was a nifty command line utility that tracked the tcp and udp conversations going on, and was simpler than ethereal, but I can't remember the name of the darned thing now...[/QUOTE]

I use ethereal and etherape as well, as I'm always curious what is going on.  Firestarter is handy because it can sit in the notification area and looking at active connections is a click away.

---

### Post by Rackerz on 2005-12-16
Thanks for the good response. I think I'll leave it off for the moment, I don't seem to have any problems.

---

