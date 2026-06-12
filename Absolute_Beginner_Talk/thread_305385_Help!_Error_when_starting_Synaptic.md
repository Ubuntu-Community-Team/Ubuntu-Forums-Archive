---
title: "Help! Error when starting Synaptic"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by antharr on 2006-11-23
When I start Synaptic Package Manager I get this message:

E: Type 'O::deb' is not known on line 38 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Could someone lead me in the right direction to correcting this problem. Thanks

---

### Post by Bachstelze on 2006-11-23
Please paste the contents of your sources.list :

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by antharr on 2006-11-23
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://getautomatix.com/apt](http://getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

O::deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main
FATAL::An apt-based error occured and installation was unsuccessful

O::deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by HokeyFry on 2006-11-23
umm i dont think that 'O::' is a valid command in sources.list. try getting rid of the 'O::' and see what happens

and also delete the line that starts with FATAL::

---

### Post by drphilngood on 2006-11-23
You could also use [source-o-matic]("http://www.ubuntulinux.nl/source-o-matic") to generate a new sources.list and then add your automatix repos to it.

This might be an easier option but HokeyFry´s fix should work.

---

### Post by antharr on 2006-11-24
Problem fixed. Thanks so much for the help guys. Removing those lines that HotFry suggested fixed it. 
This is my 3rd attempt to run Linux on my machine. I am going to stick with it this time no matter what problems I run into. With such great help that you guys supply on this forum, I don't see any reason I should have to resort to using just Windows ever again. Thanks once again.

---

