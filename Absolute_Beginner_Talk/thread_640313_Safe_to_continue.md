---
title: "Safe to continue?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-14
After installing and setting up thunderbird, i've decided i want to get rid of evolution.

Sudo aptitude remove evolution yields:

jordan@Jorcomp:~$ sudo aptitude remove evolution
[sudo] password for jordan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  evolution-exchange evolution-plugins 
The following packages will be REMOVED:
  evolution 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 8999kB will be freed.
The following packages have unmet dependencies:
  evolution-plugins: Depends: evolution (>= 2.12.1) but it is not installable
  evolution-exchange: Depends: evolution (>= 2.11.92) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
contact-lookup-applet
evolution-common
evolution-exchange
evolution-plugins
nautilus-sendto
openoffice.org-evolution
ubuntu-desktop

Score is 533

Accept this solution? [Y/n/q/?] 


Would i be killing my system by saying yes?

---

### Post by FuturePilot on 2007-12-14
Try apt-get remove instead of aptitude remove.

---

### Post by jordank on 2007-12-14
is the aptitude method harmful?

---

### Post by FuturePilot on 2007-12-14
I don't think so, but sometimes it does act a little strange like that. I'm not sure why. apt-get should just simply remove Evolution for you. The only time I use aptitude is when I'm dealing with a large number of dependencies like installing a desktop environment or something.

---

### Post by hyper_ch on 2007-12-14
you should either use aptitude or apt-get only... mixing both is not so good.

---

### Post by GSF1200S on 2007-12-14
> **hyper_ch said:**
> you should either use aptitude or apt-get only... mixing both is not so good.

Ive used both, and I havent had problems.. maybe ive been lucky? Whats bad about it? Now, Ill only use one for a program, meaning if I were to aptitude install gnomebaker, I would use aptitude to remove it. If I apt-get install gnomebaker, ill apt-get remove it, and then apt-get autoremove to remove unused packages. I look those over very carefully.

Ive heard some people objecting completely to aptitude, and some seem to praise it. I never have got a straight answer on it though..

---

### Post by CatKiller on 2007-12-14
**ubuntu-desktop** doesn't actually install anything by itself. It's a meta-package whose sole purpose is to depend on all the things that need to be included for it to be an Ubuntu desktop install. It can safely be removed.

It is possible that it would be best to reinstall the ubuntu-desktop meta-package before upgrading to later versions of Ubuntu, to aid in the upgrade process.

EDIT: aptitude and apt-get handle dependencies and suggestions differently. Whether one is better than the other depends entirely on personal preference. Mixing the two largely defeats any advantages of one of the other.

---

### Post by hyper_ch on 2007-12-14
it's just the way apt-get and aptitude handle meta-packages. For that reason it's better to use only one of them.

---

