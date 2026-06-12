---
title: "Internet Security"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by Cufishing on 2005-10-27
Does a user need to concern themselves with internet security on a Ubuntu system?

If so, what might be some of the applications available?

If there are some links somewhere, please point me in that direction. I have read a lot, and sure I have missed a lot as well. 

My other OS, loads a soft firewall, behind a hard firewall, and has two anti-spyware programs, and a anti-v running from boot. That is one of many reasons I want to break away from there. It's not like I have anything of national security, but I do on-line banking, and was wondering what is needed for this OS to continue, with peace of mind.

Thanks.

---

### Post by KingBahamut on 2005-10-27
A good firewall - firestarter 

apt-get install firestarter or search for it in Synaptic. 

As to the effectiveness of securing your box outside of that, there are a lot of things you can do. While virii and malware arent so much a concern, with a decent firewall, password security policy (changing on a regular schedule), updating via apt-get or synaptic to get security updates, that should lock you down enough to make you feel at home and relatively worry free.

---

### Post by JurB on 2005-10-27
Spyware and viruses: If you install your software only trough Synaptic there is not much to worry about , everything has been checked before it gets in the repositories. There are very little viruses out there that are written for linux, and if they were to end up on your machine they wouldn't be able to do much damage thanks to the multi user design of linux. Every major change to the system, or even installing new software, requires you to provide your password or to log in as Root user. That's why a second user account is created when installing ubuntu: one for system administration: "Root" and one to do your daily stuff.If you are on a dual boot system with windows, you can always install a virusscanner to make sure no viruses get on your windows partitions. Aegis, f-prot,....

Firewall: A native firewall service is installed and running in the background, it's acctually a set of rules called "iptables", you can easly configure them by installing a gui for it: Firestarter, Guarddog,....

---

### Post by Cufishing on 2005-10-28
Very good, thank you.

---

### Post by nitricacid on 2005-10-28
cursed be the day linux becomes global and every site installs spyware like windows.
by global I mean every house hold is using linux just the way windblows use to be.

---

