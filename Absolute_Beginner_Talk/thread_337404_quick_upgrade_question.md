---
title: "quick upgrade question"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Chmlnalien303 on 2007-01-12
well i jsut got 6.06 lts  and i was wondering if i get 6.10 iso disk will i be able to jsut put it in and reinstall? or is ther like an upgrade route? thanks , Chmln

---

### Post by CroEragon on 2007-01-12
Yes, you can reinstall to edgy but you will lose all your tweaks and program. I think that it is possible to add cd to source so when your system upgrades it read necessary data from cd. or you can do it from internet

---

### Post by Shatrat on 2007-01-12
Well, at the command line you can type 
```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Although I hear there are sometimes problems going for 6.06 to 6.10 so you should back up anything important whichever direction you decide to go.

---

### Post by MasterOfDisaster on 2007-01-12
Couple ways to do this:

1.  If your /home is on a seperate partition, you can completely reinstall the 6.10, leaving you with a fresh install with all your data and preferences.  This is almost a guarenteed success if you configure the install properly, but is not the default scheme used by Ubuntu, so disregard unless you manually set up your partitions.

2.  Take a look at this: [http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html)
Note that this can fail and leave you with a broken X server, or program, etc.  You can use this with the default Ubuntu partitioning scheme.  Use at your own risk.

And yes, you can just reinstall the 6.10 over top of the 6.06 if you would like.

---

### Post by Chmlnalien303 on 2007-01-12
well.. jsut got ubuntu 2day.. havent tweaked anything lol :D so i just was wondering whats the major diff? is eft more effecient? or just newer? thanks, ChMlN!

---

### Post by CroEragon on 2007-01-12
Dapper drake use slightly older technologies and overall it is older so it runs not as good as edgy. But Dapper got LTS (long term support, that means that ubuntu team will make bugfixes, security fixes and overall officialy support it 3 years for desktop and 5 for server and any other version of ubuntu is supported yous 18 months for desktop and 3 years for server)  and it is well tested and more stable. And got better wireless support. If yo have ubuntu to play with id and you are not afradi do reinstall it few times, use Edgy if you need stable and tested OS that just needs to be efficient than use Dapper

---

### Post by Chmlnalien303 on 2007-01-12
kk yeah i really dont have a use for this comp so im jsut ryting to expand my comp knowledge and this linus stuff is pretty neat specially ubuntu and all the buntus! thanks, CHMLN!

---

