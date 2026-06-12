---
title: "k3b and kile on ppc"
date: 2005-01-31
forum: Apple PPC Users
---

### Post by Antonius felix on 2005-01-31
Hi I have to say that ubuntu impressed me for its power. I have an ibook g4 and as soon as I heard of the power of ubuntu I erased YDL 4.0 from my laptop. And now I discovered UBUNTU!!!

I have a question: does anybody know (I do not know many things on Debian) how to install k3b and kile in ubuntu?

[I know there is an howto for k3b but it did not work: I enabled universe but still apt-get could not find the package. Maybe because there's no ppc package?]

Thanks a lot and congratulations to the ubuntu team!

  Antonio

---

### Post by usr3301 on 2005-01-31
I was able to get K3B installed and working on Ubuntu.  The "easy" way I made it work was to change the /etc/apt/sources.list file to point to the hoary packages.  Just replace all instances of warty with hoary, that will allow you to upgrade.  After doing this, I was able to do an apt-get install k3b.  In addition, I did an apt-get upgrade and an apt-get dist-upgrade to make sure I had the latest of everything else.  It worked like a champ, here are my system specs:

PowerBook G4 Aluminum
1.5GHz G4
512MB RAM
ATI Mobility Radeon 9700 /w 64MB RAM
60GB HDD

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=usr3301]I was able to get K3B installed and working on Ubuntu.  The "easy" way I made it work was to change the /etc/apt/sources.list file to point to the hoary packages.  Just replace all instances of warty with hoary, that will allow you to upgrade.  After doing this, I was able to do an apt-get install k3b.  In addition, I did an apt-get upgrade and an apt-get dist-upgrade to make sure I had the latest of everything else.  It worked like a champ, here are my system specs:

PowerBook G4 Aluminum
1.5GHz G4
512MB RAM
ATI Mobility Radeon 9700 /w 64MB RAM
60GB HDD[/QUOTE]

Be sure to start K3b with this command:

gksudo k3b

or it won't work as well.

---

### Post by val1984 on 2005-01-31
[QUOTE=poofyhairguy]Be sure to start K3b with this command:

gksudo k3b

or it won't work as well.[/QUOTE]
Starting k3b isn't the problem.
The problem is that there is no binary package for k3b on ppc :(

Maybe you should try apt-source but try googling since I don't know how to proceed ;)

---

### Post by farruinn on 2005-02-01
Much of KDE has been compiled for Ubuntu PPC however there are still some packages in Warty that are only available as source.  These commands should make k3b work without having to upgrade to Hoary.

```

$ sudo apt-get build-dep k3b
$ sudo apt-get source -b k3b

``` 

Wash, rinse, and repeat as desired =)

---

