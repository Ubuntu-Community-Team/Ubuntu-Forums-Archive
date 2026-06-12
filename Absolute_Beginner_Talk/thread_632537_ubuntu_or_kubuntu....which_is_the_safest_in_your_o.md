---
title: "ubuntu or kubuntu....which is the safest in your opinion nad why?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-05
ubuntu or kubuntu....which is the safest in your opinion nad why?

---

### Post by someoneouthere on 2007-12-05
and what are all the necessary security measures that should take after installation...?
or enable some features already build in ubuntu..?

---

### Post by rich.bradshaw on 2007-12-05
Safest doesn't really make sense. The only difference is the window manager, which is essentially the whole interface - nothing has really changed though it just looks different.

I go through phases of prefering Kubuntu and phases of prefering Ubuntu. Sometimes I even like Xubuntu, and on rare occasions Fluxbuntu.

---

### Post by Colro on 2007-12-05
They're both pretty secure out of the box. There really isn't a security difference between the two -- pick whichever one you like the most. 
It is, however, a good practice to install a firewall on either one, in my opinion at least:
```
sudo apt-get install firestarter
```

---

### Post by rich.bradshaw on 2007-12-05
There are no necessary security measures to perform - who would make an operating system that needed the user to improve upon straight away?

Oh yeah - I forget most people are used to using an OS that isn't designed to cope with the internet.

Linux isn't like windows - it has actually been thought about, there are little to no viruses - none that are "in the wild" anyway. That's because things are done differently in the Linux world so that viruses can't exist.

There are no open ports by default either - if you aren't running a server, there is no need to open ports, so it's set up with nothing listening on open ports.

Don't worry about it!

---

### Post by rich.bradshaw on 2007-12-05
> **Colro said:**
> They're both pretty secure out of the box. There really isn't a security difference between the two -- pick whichever one you like the most. 
It is, however, a good practice to install a firewall on either one, in my opinion at least:
```
sudo apt-get install firestarter
```

firestarter isn't a firewall. It's a way of configuring the firewall that is built in called iptables. There is no point in configuring it, unless you need to reconfigure it. I wouldn't bother unless you really need to filter access to a port.

i.e. you might want to only let a certain IP block connect to your computer using SSH - that's when you want to use firestarter.

---

### Post by someoneouthere on 2007-12-05
i've heard that selinux on ubuntu is by default unactive... and firestarter the latest version is on 2005...so i suppose there must be short guide of putting all this together..

---

### Post by Colro on 2007-12-05
Firestarter's still handy as it offers more security options "out of the box" then Ubuntu's default iptables configuration. ICMP filtering in particular is pretty good to have if you have no use whatsoever for any ICMP services as most people don't. 
As I said, though, it's just my opinion that's it's good practice. It's not required by any means, and an Ubuntu box is plenty secure without it.

---

### Post by rich.bradshaw on 2007-12-05
Gutsy uses apparmor instead of selinux.

Basically, if you have a router, then don't worry about firewalls on networked computers - there is no need.

As colro said, firestarter can enable ICMP filtering, but really there is no need - I wouldn't bother with adding extra stuff unless you need it, you will be overwhelmed otherwise.

Also if you set up ssh or something, you'll need to remember to reconfigure firestarter to let it work - all extra hassle, as no doubt you will forget you blocked it and you will have problems.

---

### Post by andrewoftheelves on 2007-12-05
it seems like the only way you will get a virus, is if you copy and paste malicious code yourself into your terminal, or download files from a mysterious location, so i dont think you should worry about it. haha it would be a real pain for anyone to hack linux(so i hear) and with sooo many people using windows, it would be pointless to try. like trying to skin a cat, when you can get a hairless one for free. haha peace

---

### Post by someoneouthere on 2007-12-05
under what conditions should i be concered about security? like ssh...etc
how about file sharing? usually when i check the protocols i see some suspicius "behavior" and even after i stop to share some connections are just active why?

---

### Post by Orbital75 on 2007-12-05
No security difference in Kubuntu ( KDE ) or Ubuntu ( Gnome )
these are just different versions of Ubuntu that have a different
desktop manager

---

### Post by skyjacker on 2007-12-05
> **Colro said:**
> They're both pretty secure out of the box. There really isn't a security difference between the two -- pick whichever one you like the most. 
It is, however, a good practice to install a firewall on either one, in my opinion at least:
```
sudo apt-get install firestarter
``` The firewall (Iptables) comes pre-installed, Firestarter is just a GUI to configure iptables.

---

### Post by aysiu on 2007-12-05
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

As others have said, it's not a matter of Kubuntu or Ubuntu. Those are just different faces for the same underlying structure. Both have essentially the same security framework.

---

