---
title: "Upgrade Help!"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by crapple on 2008-04-27
I am trying to upgrade from 6.6 to 8.4 but when I try to do an update the upgrade tool downloads everything but before it downloads they actual files, it gives me an error getting prerequisites failed. And the the update stops also I saw in the terminal that there was a warning failed to read mirror file.  I am running an emac with a power pc g4 processor and about 800mb of ram.

---

### Post by catalina on 2008-04-27
Hi there,

You cannot jump distributions in the upgrade.  If you are using 6.04 or 6.10 you have to install 7.04 and 7.10 before installing 8.04.

I would suggest copying your home directory or using tools such as Home backup and doing a clean install.

If you are using an older computer make sure that you have enough memory, otherwise you will have issues.  If you don't have the recommended amount of memory, download and install the "Alternate Install" which has compatible drivers for older units.

Hope this helps!

---

### Post by crapple on 2008-04-27
The thing is on they are both long term supported and it says it is possible on to upgrade from drapper to hardy.  My computer also finds 8.4 and not 6.10.  Any other ideas?

---

### Post by howlingmadhowie on 2008-04-27
if you have any software installed which you didn't install over apt, you could try removing it.

---

### Post by crapple on 2008-04-27
All I have is the software that it came with.  Then the only thing in that direction that I did was update using the update manger.

---

### Post by joninkrakow on 2008-04-27
> **crapple said:**
> The thing is on they are both long term supported and it says it is possible on to upgrade from drapper to hardy.  My computer also finds 8.4 and not 6.10.  Any other ideas?

I read somewhere from a link in one of the stickies, that if you are upgrading from the previous LTS, that you should wait a couple months--June or later, I believe--before upgrading. it didn't say exactly, but I suspect it is such an issue with making sure that everything goes well. I would wait a couple months before trying, based upon that. 

-Jon

---

### Post by crapple on 2008-04-27
I think I will try doing a fresh install.

---

