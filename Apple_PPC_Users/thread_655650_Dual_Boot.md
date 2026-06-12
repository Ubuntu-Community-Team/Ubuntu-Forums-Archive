---
title: "Dual Boot"
date: 2008-01-01
forum: Apple PPC Users
---

### Post by sleepygo on 2008-01-01
Alright, I have an imac G5 and I have it split to 2 partitions. I want to put ubuntu on the second partition and I already have leopard on the first one. I can figure out how to do it and it doesn't seem like anyone has specific directions to do so. I can't use boot camp and I have a 6.06 version of ubuntu on a cd. Any help so that I can get ubuntu would be greatly appreciated.

---

### Post by keeper of the wheel on 2008-01-01
I'm not a Mac savvy user, but on my PC I installed Ubuntu first then Windows (mainly because Windows is selfish and will not allow partitions that would leave room for competitor OS's.)
See if that works for Mac.

---

### Post by BladeMelbourne on 2008-01-01
I am dual booting Tiger and Gutsy.

I found it easiest to:
* Use the Ubuntu setup disk to partition the internal disk.
* Install OS X.
* Install Ubuntu.

The reason why I installed Ubuntu last is so that yaboot can create a boot menu that is briefly displayed when the computer starts up. This menu allows you to choose which OS you wish to boot (Mac, Linux or CD ROM).

Granted I did install both OS X and Linux on the same day - I was not concerned about blowing away my Mac partition because I had copied my Mac home directory to an external disk first.

---

### Post by samden on 2008-01-03
I have no experience with leopard, am using Panther myself but the technique is probably the same. Try booting in OSX, go into disk utility, and reformat the second partition as free space. Then boot using the Ubuntu cd, and install using the option "install in largest free space", or words to that effect.

---

