---
title: "Virtual Box Terrorist-icated my perfectly groovy new feisty box"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by rubix64 on 2007-05-07
O.K..... so maybe terorist-icated isn't a verb but still I had a perfect new feisty box running so smooth it literally purred and then I go and try to install a silly emmulator called Virtualbox and WHAM.

Now my pack-manager is wacked out and any attempt to access updates/add-remove or synaptic results in the following error msg:

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

ARRRRGGGGHHHH:mad: 

So heres the deal... I know that there are more than a few Ubuntu jedi's out there with more beans under their belt (wait a minute this is going all wrong) I mean full of beans...oh hell.... I need an Ubuntu ninja to help me figure this out.


May the ninja who helps me have a thousand fleas removed from his bedroll  so that he sleeps like a newborn kangaroo.

Excellent. Thanks

Rube

---

### Post by tgm4883 on 2007-05-07
Have you tried apt-get remove virtualbox

---

### Post by Lucifiel on 2007-05-07
Omg... yet another poor sod who got this error. 

Try this:

sudo dpkg --remove --force-remove-reinstreq virtualbox

---

### Post by rubix64 on 2007-05-07
Thanks mate, that forced removal did the trick.

cheers

---

### Post by Lucifiel on 2007-05-07
> **rubix64 said:**
> Thanks mate, that forced removal did the trick.

cheers

No problem. Man, I keep seeing posts related to this issue these days. >>;; I hope it gets fixed soon.

---

### Post by Wechuks on 2007-06-07
3 questions -
1) did Virtualbox comes with ubuntu?
2) whai it does?
3)(only if it does something important)-why removing it resolved my prolem (it was same as rubix64)?

---

### Post by steve.horsley on 2007-06-07
If you want to have another go at installing VirtualBox, try installing packages linux-headers-generic and build-essential first.

Wechuks:
VirtualBox allows one operating system to run inside another (possibly different) operating system.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

