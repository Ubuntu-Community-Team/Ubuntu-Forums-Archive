---
title: "Is it possible to install ubuntu-desktop onto Mint?"
date: 2012-12-11
forum: Any Other OS
---

### Post by dannyboy79 on 2012-12-11
I really want to use the Ubuntu Software Center to purchase RC Mini Racer but the USC isn't working within Linux Mint 14 w/ Mate so I am curious if I were to intall ubuntu-desktop and boot into the Ubuntu session, if it would be just like I installed Ubuntu 12.10 with Unity?

---

### Post by haqking on 2012-12-11
> **dannyboy79 said:**
> I really want to use the Ubuntu Software Center to purchase RC Mini Racer but the USC isn't working within Linux Mint 14 w/ Mate so I am curious if I were to intall ubuntu-desktop and boot into the Ubuntu session, if it would be just like I installed Ubuntu 12.10 with Unity?


Cant you install USC into mint ?

This is for 12 but im sure it can be adapted ?

[http://www.noobslab.com/2011/12/install-ubuntu-software-center-in-linux.html](http://www.noobslab.com/2011/12/install-ubuntu-software-center-in-linux.html)

---

### Post by dannyboy79 on 2012-12-11
i had already tried some editing of __ty__.py that didn't work, (found here: [http://forum.linuxmint.com/viewtopic.php?f=42&t=113697](http://forum.linuxmint.com/viewtopic.php?f=42&t=113697)) i'll try that later tonight after work. thanks

---

### Post by MadmanRB on 2012-12-11
Yes but you may get updates that might bug out the system.

---

### Post by dannyboy79 on 2012-12-11
here's the sources.list which appears to be all 12.10 anyway
```
deb http://packages.linuxmint.com/ nadia main upstream import
deb http://archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ quantal partner
deb http://packages.medibuntu.org/ quantal free non-free
```
except for medibuntu (which I normally use with ubuntu anyway) and the linuxmint line

I just can't believe the Ubuntu Software Center doesn't work with Linux Mint. All I want is to buy RC Mini Racer here: [https://apps.ubuntu.com/cat/applications/decane-rcminiracers/](https://apps.ubuntu.com/cat/applications/decane-rcminiracers/)
but this window pops up when i click on it.
[IMG]https://lh3.googleusercontent.com/-2xM907tqft4/UMfupO6_xaI/AAAAAAAAAsM/KPbdsqer9uA/s455/Screenshot-1.png[/IMG]
and then it merely opens google chrome web browser with nothing.

---

### Post by BertN45 on 2012-12-11
I did it the other way around without any problem, I installed the cinnamon desktop in Ubuntu 12.10.

---

### Post by Chdslv on 2012-12-11
> **dannyboy79 said:**
> here's the sources.list which appears to be all 12.10 anyway
```
deb http://packages.linuxmint.com/ nadia main upstream import
deb http://archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ quantal partner
deb http://packages.medibuntu.org/ quantal free non-free
```

Of course you can!

Add to your sources.list

> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal -updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal -updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal -backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal -backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal -security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal -security main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal  partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal  partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal  main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal  mainand then, put '#' in front of the nadia repo, so that it won't trouble the update and installing--you can take it off later if you want.

> sudo apt-get update
sudo apt-get install unity software-centerLog off and log in to Ubuntu and then go on to install anything you want, the Quantal users are free to do so, whilst the Mint users are disallowed.

Good day!

Ch

---

