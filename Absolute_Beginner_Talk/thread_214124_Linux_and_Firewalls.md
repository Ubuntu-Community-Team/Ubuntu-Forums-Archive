---
title: "Linux and Firewalls?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by mcdrake on 2006-07-12
Hey guys!

To be able securing my ubuntu system which firewall would be recommend? 

Maybe there is already a built in firewall included? 

Any help is greatly aprechiated. 

Cheers, 
McDrake

---

### Post by T700 on 2006-07-12
If you are behind a NAT enabled router and you are at average risk, it is not necessary, in my opinion.  That said, it certainly doesn't hurt to run a firewall.  Two good, graphical interfaces, for the built in functionality are Firestarter and Guard Dog.  Both are available via aptitude or Adept.

Paul

---

### Post by timetunnel on 2006-07-12
Package "firestarter" is a firewall with a graphical interface for configuration. All outbound traffic is allowed and all inbound traffic forbidden in the default settings. The firewall will be up and running though you won't see an icon or even a process in the system monitor.

---

### Post by siccness on 2006-07-12
Just remember, a poorly configured Firewall is worse than no firewall at all.

---

### Post by T700 on 2006-07-12
> **siccness said:**
> Just remember, a poorly configured Firewall is worse than no firewall at all.

How so?  If you have no firewall, your vunerability would be 100%.  If poorly configured, your vunerability might be 99% or even still 100%, but I'm not clear how it could be worse.

Paul

---

### Post by siccness on 2006-07-12
> **T700 said:**
> How so?  If you have no firewall, your vunerability would be 100%.  If poorly configured, your vunerability might be 99% or even still 100%, but I'm not clear how it could be worse.

Paul

Eek, my apologize. Yeah, what I meant to say is a poorly configured firewall won't necessarily be any better than without.

---

### Post by mcdrake on 2006-07-14
hi guys!
ok, thanks for the info! 
i'll check it out.
mcdrake

---

### Post by FredB on 2006-07-14
> **timetunnel said:**
> Package "firestarter" is a firewall with a graphical interface for configuration. All outbound traffic is allowed and all inbound traffic forbidden in the default settings. The firewall will be up and running though you won't see an icon or even a process in the system monitor.

Indeed. And it is a good set for most people. As long as you don't install software from strange places.

---

