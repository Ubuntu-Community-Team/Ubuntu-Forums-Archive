---
title: "can't update update manager!"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by mannock on 2007-06-09
i want to go from ubuntu  6.10 to 7.04   but apparently i first need to upgrade the update manager from   0.42.2    to 0.45.2  .          trouble is,  it does not appear in the list of packages even with all repositories enabled.   all i get is the old one.

---

### Post by diatribe on 2007-06-09
try running: 
update-manager -c -d
if that does not work, you could just replace any instance of edgy with feisty in your sources.list and upgrade that way

---

### Post by zvacet on 2007-06-09
```
sudo aptitude update
```

---

### Post by mannock on 2007-06-10
tried both of those without success.   it says my system is up to date which is obviously wrong.    so how do i replace edgy with feisty in my sources list?

---

### Post by anaconda on 2007-06-10
> **mannock said:**
> i want to go from ubuntu  6.10 to 7.04   but apparently i first need to upgrade the update manager from   0.42.2    to 0.45.2  .          trouble is,  it does not appear in the list of packages even with all repositories enabled.   all i get is the old one.

Sounds like you have edgy:s repositories, and thet the new update manager is only available in feistys repositories..

I dont know, but that is my guess..

---

### Post by mannock on 2007-06-10
i suppose i had better check exactly what version i have.   on boot it says 2.6.15-28-k7
assuming this is edgy,   how do i get the feisty repositories?

---

### Post by zvacet on 2007-06-10
Well it is not recommended way to do but 

[https://help.ubuntu.com/community/FeistyUpgradesManual]("https://help.ubuntu.com/community/FeistyUpgradesManual")

---

