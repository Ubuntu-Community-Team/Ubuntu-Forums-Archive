---
title: "[SOLVED] 7.04 to 7.10"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-10-18
I have my Feisty the way I like it. I have removed the ubuntu-desktop package along with a bunch of others that I was not using.

Now, if I want to upgrade to Gutsy, do I have to install all the packages before hand, or will clicking on the upgrade button take care of it.

I am going to remove ubuntu-desktop later anyway, since I don't use Evolution and a couple other pre-installed apps.

If I have to install all the packages and make Feisty "standard" before upgrading to Gutsy, that's where the problem arises, that I do not remember which packages I removed and what is "standard"

Has anyone upgraded when they had removed ubuntu-desktop or any other pre-installed package?

---

### Post by Archmage on 2007-10-18
Simply install ubuntu-desktop with APTITUDE and after upgrade remove ubuntu-desktop with APTITUDE.

Aptitude will remove all packages that it installed because of ubuntu-desktop, when you remove ubuntu-desktop.

---

### Post by Beggar on 2007-10-18
Someone wiser then me might disagree, but I dont think ubuntu-desktop is needed for the upgrade to gutsy. As long as you have ubuntu-minimal installed, it should upgrade fine, however you might not get some of the new desktop stuff, compiz-fusion, that really annoying search tool, etc. automatically, without the dependancy from ubuntu-desktop you will have to manually install it.

---

### Post by Inxsible on 2007-10-18
> **Archmage said:**
> Simply install ubuntu-desktop with APTITUDE and after upgrade remove ubuntu-desktop with APTITUDE.

Aptitude will remove all packages that it installed because of ubuntu-desktop, when you remove ubuntu-desktop.

Right. But I was hoping there was a way around that. 

Oh well.

---

### Post by Inxsible on 2007-10-18
> **Beggar said:**
> Someone wiser then me might disagree, but I dont think ubuntu-desktop is needed for the upgrade to gutsy. As long as you have ubuntu-minimal installed, it should upgrade fine, however you might not get some of the new desktop stuff, compiz-fusion, that really annoying search tool, etc. automatically, without the dependancy from ubuntu-desktop you will have to manually install it.

See thats the thing. If the new features like the desktop search tool depends on ubuntu-desktop, I will have to keep u-d around. But if the tool is annoying as you say, all bets are off :D

---

### Post by Beggar on 2007-10-18
No, it doesnt depend on u-d. u-d is a metapackage that depends on everything that they want to install by default. You can still install those program manually, it just wont install automagically on the upgrade.

ud depends on tracker tool, pidgin, etc.

nothing should depend on u-d (it doesnt actually do anything, other then work as a common build).

---

