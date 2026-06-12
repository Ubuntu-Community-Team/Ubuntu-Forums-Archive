---
title: "firewall?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by harry rao on 2008-03-18
hi,
i'm trying to use azureus to download some files,
i'm not sure whether there's a firewall set up - could anyone provide a command and/or advice to search for firewall settings and deactivate it.

-harry.

---

### Post by supertails on 2008-03-18
If you have Ubuntu you don't need firewalls or AV protection.

---

### Post by dsauxier on 2008-03-18
to see if you have a firewall enabled : 
```

sudo iptables -L

```
If the results look like this, then you don't have a firewall enabled :
[INDENT]Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     [/INDENT]

---

### Post by Papa-san on 2008-03-18
There isn't a firewall per-se... Do a search on 'IPtables' and you'll find out what it does and whether or not it's interfering with your program. (Unlikely) However, I'll defer to someone who knows more.
Someone should be able to recommend some commands to check.

Like dsauxier, above!   :-D

---

### Post by JoshuaRL on 2008-03-18
> **supertails said:**
> If you have Ubuntu you don't need firewalls or AV protection.

That is not correct.  You do not need Anti Virus currently because there is no active Linux malware in the wild.  However, you do need and have an excellent firewall.  Its called iptables, and it comes installed and configured automatically.  And if you installed a bittorrent client it should configure iptables for you.

What errors do you have?

---

### Post by nick_h on 2008-03-18
Ubuntu comes with a firewall called iptables installed by default.  However, it won't have any rules defined by default.  You can look at the rules by typing:
```
sudo iptables -L
```
See the manual page for details:
```
man iptables
```
If you want to use the firewall I suggest you install a front-end to iptables such as Firestarter.

---

### Post by supertails on 2008-03-18
I know about Iptables. I was just saying you don't need 3rd party firewalls.

---

### Post by NightwishFan on 2008-03-18
Configure a few options in firestarter and you can get a true stealth rating at Shields Up.

---

### Post by JoshuaRL on 2008-03-18
[Some good reading for security concerns.](http://ubuntuforums.org/showthread.php?t=694198)

supertails:  Yeah, I thought so.  I just came across a little strong because I wanted to get the right point across to the OP.

---

