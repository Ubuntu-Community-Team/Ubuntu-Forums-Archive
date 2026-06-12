---
title: "The following packages have been kept back...why?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-08-03
The last few times I've tried to update I get a message about a package (totem) being "kept back." What causes a package to be kept back? What should be done about it?

---

### Post by Ziox on 2006-08-03
> **pbaehr said:**
> The last few times I've tried to update I get a message about a package (totem) being "kept back." What causes a package to be kept back? What should be done about it?

A package could be kept-back because it involves system changing results.  In other words, it would modify other parts of the system. To do a "full update" use this command:

sudo aptitude dist-upgrade

---

### Post by pbaehr on 2006-08-03
I tried both upgrade and dist-upgrade and they both hold the package back. Actually, I never really understood the difference between upgrade and dist-upgrade so if someone wants to mention that, too, that would be cool.

**** EDIT: I take that back, when I read your comment more carefully I tried "aptitude" instead of "apt-get" it not only upgraded the totem package, but removed some old stuff. Should I stop using apt-get?

---

### Post by Ziox on 2006-08-03
> **pbaehr said:**
> I tried both upgrade and dist-upgrade and they both hold the package back. Actually, I never really understood the difference between upgrade and dist-upgrade so if someone wants to mention that, too, that would be cool.

**** EDIT: I take that back, when I read your comment more carefully I tried "aptitude" instead of "apt-get" it not only upgraded the totem package, but removed some old stuff. Should I stop using apt-get?

apt-get and aptitude is basically the same function, except that aptitude handles dependencies much better.  So using aptitude to install items will install all the dependencies along with it, making it much easier for everthing actually...

I personally would advice to use aptitude, but it is up to you.

---

### Post by SyncMaster on 2008-05-29
I have a 7.10 server and to resolve this issue I did

sudo apt-get install openssh-blacklist

and then it installed the openssh-client and server. Somewhere I found a post that these two rely on the blacklist.

Gruess
Rainer

---

### Post by neurostu on 2008-05-29
```

sudo apt-get upgrade

```
I believe this upgrades all available packages WITHIN the current distrobution
```

sudo apt-get distro-upgrade

```
upgrades from one distro to another

I could be wrong though...

---

### Post by chagocota on 2008-05-31
apt-get install openssh-blacklists, then apt-get upgrade.

That fixed the problem on my NSLU2.  Thanks SyncMaster!

---

### Post by sanus|art on 2008-06-01
Some packages may appear as 'kept back' in case of not fully update integration. 

e.g. Open office usually being kept back until currently installed language packs for the current version of it are in the repositories.

---

### Post by skaboobie on 2008-07-24
> **chagocota said:**
> apt-get install openssh-blacklists, then apt-get upgrade.

Note that the package name is openssh-blacklist, without the plural "s" at the end.

---

