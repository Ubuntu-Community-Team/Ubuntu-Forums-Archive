---
title: "[SOLVED] what happens if one upgrades a linux distro?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-03-27
i was just wondering if somebody upgrades ubuntu to a newer version, then does all his data on the computer gets lost after the upgrade? anybody with the answer?:confused:

---

### Post by saj0577 on 2008-03-27
Not if you update throught the update manager.

Saj

---

### Post by sumguy231 on 2008-03-27
If you use the update manager to upgrade to the next version, your data and most configuration will stay put.

---

### Post by bhadotia on 2008-03-27
OK, i get now- if we use the update manager then all our settings, documents etc. stay put even after an upgrade . Thanx guys!:)

---

### Post by saj0577 on 2008-03-27
Yep extreamly unlikely you will lose your files.
You should try to back up your files often anyway.
Please mark as solved.

Saj

---

### Post by philinux on 2008-03-27
Consider putting home on its own partition. Then re-installs are much easier as the /home partitoin is not formatted.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by (((X))) on 2008-03-27
Settings are all located in your home directory and are hidden, I don't thing update manager will affect them.
Anyway create  backups.

---

### Post by Oldsoldier2003 on 2008-03-27
> **philinux said:**
> Consider putting home on its own partition. Then re-installs are much easier as the /home partitoin is not formatted.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I concur. also makes life easier when you run two three four ...fifteen different distros on your machine

---

### Post by chlorinekid on 2008-03-27
> **Oldsoldier2003 said:**
> I concur. also makes life easier when you run two three four ...fifteen different distros on your machine in what what way exactly? not disagreeing, im just curious! :)

---

### Post by Oldsoldier2003 on 2008-03-27
> **chlorinekid said:**
> in what what way exactly? not disagreeing, im just curious! :)

you dont have to remember where to save stuff to make it accessible to your other distros, I make a data partition and symlink it to /home and as long as your distros are of the same family the configs seem to work fine.

One thing that would seem smart when running multi distros is to have a shared /boot directory... in a word **DON'T**, because you'll be sorry if you do it and mix RH variants with debian variants.

---

### Post by bhadotia on 2008-04-17
My root partition has only 2.5 GB of space left , will it be enough for the upgrade .


Also, (again) what will happen to all the software that I have installed, and the extra repos that I have added (and all other stuff relating to the system administration etc.,etc.....) will they also be automatically upgraded (updated)  according to the new version OS.



One more thing, is there any way in which we can resize the root partition (through live cd or something like that ) my root partition is 9.5 GB . Or is this much enough for all my purposes?


Many thanx.

---

