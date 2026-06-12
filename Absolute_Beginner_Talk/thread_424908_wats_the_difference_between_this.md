---
title: "wats the difference between this?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by chakkaradeep on 2007-04-27
**sudo apt-get update**
**sudo apt-get upgrade**

AND

**sudo aptitude update**
**sudo aptitude upgrade**

??

---

### Post by PartisanEntity on 2007-04-27
apt-get and aptitude are two different package managers. Aptitude keeps a history of the files and dependencies you have downloaded, apt-get does not.

The benefit of aptitude is that you can later delete unwanted packages and their dependencies to reclaim space.

---

### Post by wormser on 2007-04-27
> **PartisanEntity said:**
> apt-get and aptitude are two different package managers. Aptitude keeps a history of the files and dependencies you have downloaded, apt-get does not.

The benefit of aptitude is that you can later delete unwanted packages and their dependencies to reclaim space.

I always thought that apt-get and aptitude were the same thing.  So, why would you use apt-get if aptitude can delete unwanted packages?  Is apt-get an earlier version?

---

### Post by jonathan21 on 2007-04-27
sudo apt-get update is usually used when you wanna see the latest updates for your version of ubuntu.

sudo apt-get upgrade is used to upgrade programs so they are compitable with a new version of ubuntu.

sudo aptitude update is the same as apt-get.

---

### Post by chakkaradeep on 2007-04-27
> **jonathan21 said:**
> sudo apt-get update is usually used when you wanna see the latest updates for your version of ubuntu.

sudo apt-get upgrade is used to upgrade programs so they are compitable with a new version of ubuntu.

sudo aptitude update is the same as apt-get.

I was actually asking the difference between the usage of **apt-get** and **aptitude** and not about **update** and **upgrade** :D 

Why there exists two programs ?

---

### Post by Bloch on 2007-04-27
apt-get update  does not change your system - it only updates the list of software. That's why it only takes a few seconds.

apt-get upgrade  upgrades every package to the latest version, so you should enter apt-get update first so your list is the curent one.

These are done automatically by the "updates" facility in Ubuntu - you know the little icon that appears when new software is available.

Synaptic is a GUI interface to apt-get. It's handy because you can search the repositories and read a brief description of what each piece of software can do. It does nothing more than what apt-get does. People on the forums generally give instructions like:```
 apt-get install mplayer 
```  rather than telling people to open Synaptic etc.

I'm sure people will disagree, but I don't see any need for a normal user to use aptitude. If you like to experiment with different software and repositories, installing it and uninstalling it some time later, then you might prefer aptitude.

---

### Post by chakkaradeep on 2007-04-27
> **Bloch said:**
> apt-get update  does not change your system - it only updates the list of software. That's why it only takes a few seconds.

apt-get upgrade  upgrades every package to the latest version, so you should enter apt-get update first so your list is the curent one.

These are done automatically by the "updates" facility in Ubuntu - you know the little icon that appears when new software is available.

Synaptic is a GUI interface to apt-get. It's handy because you can search the repositories and read a brief description of what each piece of software can do. It does nothing more than what apt-get does. People on the forums generally give instructions like:```
 apt-get install mplayer 
```  rather than telling people to open Synaptic etc.



No, again you are not getting what I had asked :) 

This is not for what you mean by an **update** and **upgrade** processes , rather the difference between **apt-get** and **aptitude**.

And yes, I do know what happens when you do update and upgrade, but why we use TWO PROGRAMS CALLED apt-get AND aptitude

---

### Post by PartisanEntity on 2007-04-27
I prefer aptitude since it keeps track of what has been downloaded and this feature is great for when you want to completely purge files and packages.

---

### Post by PartisanEntity on 2007-04-27
> **chakkaradeep said:**
> No, again you are not getting what I had asked :) 

This is not for what you mean by an **update** and **upgrade** processes , rather the difference between **apt-get** and **aptitude**.

And yes, I do know what happens when you do update and upgrade, but why we use TWO PROGRAMS CALLED apt-get AND aptitude

Here you go:
[http://en.wikipedia.org/wiki/Aptitude_%28program%29](http://en.wikipedia.org/wiki/Aptitude_%28program%29)

---

### Post by chakkaradeep on 2007-04-27
> **PartisanEntity said:**
> Here you go:
[http://en.wikipedia.org/wiki/Aptitude_%28program%29](http://en.wikipedia.org/wiki/Aptitude_%28program%29)

Thanks, but any idea on how to bring the [front-end]("http://en.wikipedia.org/wiki/Image:Aptitude.png")

---

