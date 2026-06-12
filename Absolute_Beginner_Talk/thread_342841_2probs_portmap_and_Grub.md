---
title: "2probs: portmap and Grub"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2007-01-20
Being happy that i now can recognize my NSLU2,
i still find it quite unusable :roll: 

First of my problems:

I can't start nfsd anymore on my NLSU2 (it's a debian now). The problem is that portmap doesn't does it job nomore..

Whenever i try to start nfs-kernel-server, it "hangs" with the nfsd.
Nfsd then "hangs" again on starting/stopping portmap. Trying to reinstall portmap, the NSLU2 hangs on stopping portmap.
Sure, why not kill portmap first? Done that, but the problem still remains that portmap has to be started when it's installed, and apt-get hangs when it tries to start it.

How can i make my nfs work again?

Second problem:
i installed Sabayon, and i now have 3 OS'es on my pc. (Kubuntu, Xp, Sabayon)
How come i can't boot Sabayon by just copying the boot entry from his /boot/grub/menu.lst,
and add it into my Kubuntu's one?


Iarwain

---

### Post by Iarwain ben-adar on 2007-01-21
Bumping it to the top :D


Iarwain

---

