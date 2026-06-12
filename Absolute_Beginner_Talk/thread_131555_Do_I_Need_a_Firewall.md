---
title: "Do I Need a Firewall?"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by wsmoser2004 on 2006-02-16
The title pretty much sums it up.  I know that I don't need a virus scanner, but do I need a firewall?  I was reading somewhere (possibly on these forums?) about someone that had a trojan on their system when running Ubuntu.  I'd like to avoid that if at all possible.

If the answer is "Yes, you should have a firewall", what is the name of the program I should get?  I use both wireless and wired connections; I assume the firewall would take care of both...?

Thanks for any insight you might have.

---

### Post by SMF on 2006-02-16
The firewall can be found on the left top corner of your desktop
Applications/System Tools/Firestarter

I seen a Anti-V progy in the add Applications menu but I forgot where I seen it.

:confused:

PS a anti-v scanner can be found in the add applications:
Add Applications/Accessories/More Programs/ Aegis

---

### Post by Lord Illidan on 2006-02-16
I think you definitely should use a firewall. Linux or not, you are not safe out there without one. 

If you use GNOME - (ubuntu) then use firestarter ```
sudo apt-get install firestarter
```. 

If you use KDE - (kubuntu), then use guarddog ```
sudo apt-get install guarddog
```

---

### Post by piedamaro on 2006-02-16
A firewall is not essential if you have no open ports (i.e. no services running in background accepting connections).
Ubuntu doesn't run any service accepting outside connections by default (iirc).
You can run "netstat -tuan" and see.

---

### Post by psusi on 2006-02-16
Firewalls are only needed to block access to ports you don't want certain people to be able to connect to.  By default ubuntu doesn't have any open ports, so there's nothing to block.

---

### Post by Brokenrgv on 2006-02-16
just installed aegis, how do you start the thing ? looked everywhere

---

### Post by wsmoser2004 on 2006-02-16
OK, thanks for the info.  I am running Kubuntu (sorry, I left out that piece of information) so I will probably use guarddog.  I don't THINK I have anything running that has open ports, but I'd feel safer with a firewall....I may even give the virus scanner a shot.  

I'm currently in Windows, so I'll try this out the next time I boot into Kubuntu....

---

### Post by fredtal on 2006-02-17
A router makes a nice firewall.  It will block incoming but will not outgoing.  But you can watch the blinking lights, and see what's happening and take action if you suspect something funny is going on.

---

### Post by wsmoser2004 on 2006-02-17
Yes, I am in fact behind a router most of the time...at home, I have a router with a firewall, and when I'm at school, my school has a firewall.  But just in case I'm ever somewhere without one....

---

