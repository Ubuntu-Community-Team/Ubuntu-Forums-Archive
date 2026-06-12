---
title: "Dist-Upgrade leaves out packages"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-03-28
Considering that a new version of Ubuntu is released every 6 months, I think it's important to be able to upgrade rather then re-installing each time as I have so far.

However I've noticed a few problems with the dist-upgrade process.



For example, upgrading from dapper to edgy. A fresh Dapper install (from cd) has the linux-386 kernel installed. A fresh Edgy install (from cd) has linux-generic.

So why then, when I dist-upgrade from dapper to edgy, do I not get linux-generic installed?

I've also noticed heaps of other minor things. Like the console font. When in tty1-6, Edgy installed from cd has a nice crisp clear thin font. Dapper installed from cd does not have this font. Edgy upgraded from Dapper does *not* have this font.

I understand that these could be considered relatively minor issues, but I would really prefer to know that I'm getting all the new packages when I dist-upgrade.


Any suggestions?

---

### Post by Bachstelze on 2007-03-28
As the name says, dist-upgrade upgrades your packages, it doesn't install new ones - unless required by dependencies.

---

### Post by easyease on 2007-03-28
I always like a fresh from cd install of the latest version of ubuntu, cant go wrong as long as you have a  seperate home partition. using apt to upgrade is always a gamble in my view.

---

### Post by dr_d on 2007-03-28
> As the name says, dist-upgrade upgrades your packages, it doesn't install new ones - unless required by dependencies

No wonder!! I never realized this. In this case aptitude/apt is a absolutely terrible way to upgrade.

Does the update-manager -c method install new packages? (yes, i know it's called the *update* manager, but damn, there must be SOME way to get a decent upgrade around here).

---

### Post by dr_d on 2007-03-28
anybody? know how to upgrade and get the new packages aswell?

this is really bad. i think i might file a bug soon, because imo this should be brought to the developers attention.

re-installing every 6 months is not an option for me... ideally i'd like to get a good system set up and then never re-install again. well, maybe in like 10 years, but yeah you get the idea.

---

### Post by zvacet on 2007-03-29
You don´t have zo reinstall every 6 months.If your distro version serves you well stick with it as longas you can get updates for it (suport time).After that you can do fresh install of newest version.

---

### Post by dr_d on 2007-03-30
sure, but wouldn't it be nicer never to have to re-install?

with other OS such as windows, it's unlikely that this will ever be possible. microsoft is generating a lot of revenue from vista sales, and in five years time they will want to do it again.

with linux, it would be possible. in fact because everything is already separated into packages, i'm guessing that this goal is tantalizingly close.

am i the only one who wants this?

---

### Post by dr_d on 2007-03-31
is there some way i can get a list of all the packages on a system?

then i could install the new packages manually :)

---

