---
title: "How to open ports"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by g99 on 2006-12-23
Hi!

I installed ubuntu a few days ago,and i'm not connectable when use bittorrent downloads,because i can't open the port which the client uses. :-k 
please help me how to do it! thx

---

### Post by xpod on 2006-12-23
Hi & welcome to the forums.
Im just starting to learn about torrents and ports etc myself so i cant be too specific but ubuntu`s firewall is called iptables and it`s already installed by default.
You can install a gui frontend for it by installing "firestarter" from synaptic or typing ...

```
sudo aptitude install firestarter
```

In the terminal.
It`s pretty straightforward to set up whatever "policys" you want from there.

Cant tell you much more as it`s all still a bit gobbildygook to me too:D 
Good luck

EDIT:Applications>accessories>terminal......or system>administration>synaptic
Just in case:-)

---

### Post by rowanparker on 2006-12-23
Or are you using a router?

---

### Post by g99 on 2006-12-23
Yes, Im using a router and i've already installed Firestarter.

---

### Post by rowanparker on 2006-12-23
You'll need to logon to the router and open up the ports then.

---

### Post by 3rdalbum on 2006-12-23
Ubuntu's firewall isn't configured by default - your router must contain a firewall that is blocking the port.

If you can't find your router's documentation, try going into Firefox and accessing the address:

[http://192.168.1.1](http://192.168.1.1)

---

### Post by Cardmaster91 on 2006-12-23
aye, i have a similar problem. im using azureus, and i have opend the ports on my router, but it continues to give me a nat error, and says im behind a firewall. i used portforward.com to open the ports

---

### Post by az on 2006-12-23
> **g99 said:**
> 
I installed ubuntu a few days ago,and i'm not connectable when use bittorrent downloads,because i can't open the port which the client uses. :-k 
please help me how to do it! thx

You don't need to open ports.  If you install something that is listening, the port is open.  You do not need to install firestarter - by default nothing is blocked.

You don't need to go around playing with firewall rules to protect a desktop system.  That's useless.

As stated, you will need to make your router route the ports to your ubuntu box, though.  Usually, the application's documentation will detail how to configure your router.

---

