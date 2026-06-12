---
title: "Beryl to remove for Feisty"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Village on 2007-04-28
I put Beryl on my computer when I installed 6.10 (now running Kubuntu, but I also have Ubuntu on it). 

Anyway Berly has for a while at least not been working that well, so I turned it off and let KWin do the job. 

Now the time has come to upgrade to Feisty I've heard a lot of good things so I want to upgrade. The question is should I try to remove Beryl so that when I upgrade I can then put Beryl on again, or let the upgrade go though and hope for the best.

Also I don't know how to remove Beryl as it does not appear in the add/remove programs under either Kubuntu or Ubuntu.

Thanks for any advice,

Village

---

### Post by lepz on 2007-04-28
I had issues with beryl when I done an upgrade from dapper > edgy, done a re-install for feisty so dont know. But if you want to remove.

sudo apt-get --purge remove beryl* emerald* libberyl* libemerald*
sudo apt-get --purge autoremove
sudo apt-get autoclean

rm -r ~/.beryl
rm -r ~/.emerald
rm -r ~/.beryl-managerrc

---

