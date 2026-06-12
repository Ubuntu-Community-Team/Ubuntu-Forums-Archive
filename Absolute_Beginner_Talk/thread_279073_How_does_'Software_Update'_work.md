---
title: "How does 'Software Update' work?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by mikeymikec on 2006-10-17
I've had an install of Ubuntu on my laptop for a few months now, and the software update function seems to be working, ie. at least every week there are about 10 updates that it suggests should be installed.

I'm just wondering, why is OpenOffice still on 2.0.2?  .3 has been released for some time now, and .4 has recently been released.  It's not that I'm an update/upgrade junkie, just that in the particular case of OpenOffice 2.0.2 had bugs in that affected my work (re: PDF export) which are fixed in 2.0.4.

There seems to be no option in the add/remove programs UI to install a newer version of OO.

---

### Post by Bachstelze on 2006-10-17
Because the Update Manager only loks for software on the repos you have activated. By default, you only have the official Ubuntu repos and versions of OOo > 2.0.2 have not been packaged on them. Of you really wan the latest, you can either install it from source or search for a repo with a packaged version of it available.

---

### Post by Arby on 2006-10-17
Someone else can probably give a more detailed answer but in general there is often a lag between developers releasing a new version of a piece of software and it becoming available in your favourite distro.

I think it is to do with the time taken to get a new release packaged up as an ubuntu style .deb and getting it to work correctly with the ubuntu way of doing things versus the Suse/fedora/other distro way of doing things. Since I never deal with packaging software I may be completely wrong though. I'm sure some nice person is beavering away to get an ubuntu package of the latest open office ready, give em time:) 

Of course if you *really* want 2.0.4 you could always go get it from the open office site and install it manually:)

---

### Post by Bachstelze on 2006-10-17
Just as info : OOo 2.0.4 will be in Edgy, so I guess it's just not worth it building a Dapper package now.

---

### Post by TheWizzard on 2006-10-17
> **HymnToLife said:**
> Just as info : OOo 2.0.4 will be in Edgy, so I guess it's just not worth it building a Dapper package now.

dapper is "long term support". 
software updates are released frequently. it just takes time for the developrs to make a package that is stable, etc. 

i wouldn't advice to do a manual installation, though. at least if you're not planning to do a re-install in the next few years. 
waiting for the official releases is the best if you want long term stability. 

if you want bleeding edge software, try edgy.

---

### Post by jeffathehutt on 2006-10-17
Once a release (such as Dapper) is declared stable, only bug fixes and security fixes will ever make it into the official repositories.  No new packages are going to be added because they could disrupt the stable operating system.

---

### Post by mikeymikec on 2006-10-17
Is there a user-friendly way of upgrading Ubuntu to the latest release then?

Otherwise it seems a bit silly to put any software into a distro that evolves quickly.

---

### Post by jeffathehutt on 2006-10-17
> **mikeymikec said:**
> Is there a user-friendly way of upgrading Ubuntu to the latest release then?

Sure, you can use the built in update-manager to upgrade, or you can use synaptic, or aptitude.  There is no need to reinstall the entire system each time there is a new release.

---

### Post by dannyboy79 on 2006-10-17
> **jeffathehutt said:**
> Sure, you can use the built in update-manager to upgrade, or you can use synaptic, or aptitude.  There is no need to reinstall the entire system each time there is a new release.

This answer is not true. Dapper will never have the version of Open Office that this guy is asking about in it's repos. In fact you're the one that stated the only security updates and bug fixes will be released into the repos and not EVERY package update that gets released.

I take this back, you can "upgrade" dapper to meet the latest release of "edgy" by updating your sources.list and then doing a sudo aptitude dist-upgrade, I THINK? but as far as "updating" packages that are in Dapper, that's the release they'll stay at unless like he said, a bug or a security update.

---

### Post by jeffathehutt on 2006-10-17
> **dannyboy79 said:**
> This answer is not true. Dapper will never have the version of Open Office that this guy is asking about in it's repos. In fact you're the one that stated the only security updates and bug fixes will be released into the repos and not EVERY package update that gets released.

I take this back, you can "upgrade" dapper to meet the latest release of "edgy" by updating your sources.list and then doing a sudo aptitude dist-upgrade, I THINK? but as far as "updating" packages that are in Dapper, that's the release they'll stay at unless like he said, a bug or a security update.

Sorry, I don't think I was clear about that.  I'm not talking about upgrading Dapper, I'm talking about upgrading to Edgy once it becomes stable.  Dapper will never get new versions of software, but Edgy will ship with newer versions once it is released.  After Edgy is released, it's the same situation over again.  No new packages will be added to Edgy after the release time.

---

### Post by TheWizzard on 2006-10-17
> **dannyboy79 said:**
> This answer is not true. Dapper will never have the version of Open Office that this guy is asking about in it's repos. In fact you're the one that stated the only security updates and bug fixes will be released into the repos and not EVERY package update that gets released.

I take this back, you can "upgrade" dapper to meet the latest release of "edgy" by updating your sources.list and then doing a sudo aptitude dist-upgrade, I THINK? but as far as "updating" packages that are in Dapper, that's the release they'll stay at unless like he said, a bug or a security update.

are you sure about this? i'm running dapper for a few months now and new releases of software are appearing in the repo's all the time. not just bug fixes and security updates! 

examples:
amarok, flash, k3b, kopete. 

besides, before ubuntu i used fedora. different versions on different computers. but on both computers the same software versions. one time even a complete new version of kde! 
the only differences between fedora core 3 or core 5 were
- improvements in the installation process
- less downloading after the installation because software was more up-to-date
but in the end no differences in the versions of the software packages! 


maybe you're right, but i can't see why a new version of open office is not released through the dapper repo's. 


ps i keep my pc up-to-date with the folowing script in /etc/cron.daily


```
#!/bin/bash

apt-get -y update 
apt-get -y upgrade 
```

forward root's mail to a gmail account and you'll keep informed on what's going on on your boxes.

---

### Post by mikeymikec on 2006-10-18
> **TheWizzard said:**
> are you sure about this? i'm running dapper for a few months now and new releases of software are appearing in the repo's all the time. not just bug fixes and security updates! 

```
#!/bin/bash
apt-get -y update 
apt-get -y upgrade 
```


I tried these two commands on their own, and they found no updates to install.  I went into 'software properties' in the admin menu, ticked all the boxes (there seems to be little to tell them apart), tried those commands again, and what seemed like a few small programs were updated.  I checked the synaptec software package manager, but it didn't list anything more than OO 2.0.2, and 'force upgrade' didn't list any later versions.

---

### Post by dannyboy79 on 2006-10-18
> **TheWizzard said:**
> are you sure about this? i'm running dapper for a few months now and new releases of software are appearing in the repo's all the time. not just bug fixes and security updates! 

examples:
amarok, flash, k3b, kopete. 

besides, before ubuntu i used fedora. different versions on different computers. but on both computers the same software versions. one time even a complete new version of kde! 
the only differences between fedora core 3 or core 5 were
- improvements in the installation process
- less downloading after the installation because software was more up-to-date
but in the end no differences in the versions of the software packages! 


maybe you're right, but i can't see why a new version of open office is not released through the dapper repo's. 


ps i keep my pc up-to-date with the folowing script in /etc/cron.daily


```
#!/bin/bash

apt-get -y update 
apt-get -y upgrade 
```

forward root's mail to a gmail account and you'll keep informed on what's going on on your boxes.

I should have been more clear. In debian, and ubuntu, once the OS is released, the packages are "frozen" until the next stable release. This helps to keep the OS stable. Throwing in new packages here and there could cause instablility. Debian is one of the most stable OSs around. NASA has used it for experiments on the space shuttle, because you just can't go into space easily to repeat the experiment if it crashes.
Important security fixes are updated though, in both ubuntu and debian. **BUT** if you enable OTHER non-default repos than you'll get packages updated that could possibly BREAK your system. Sometimes they aren't the latest and greatest though.

---

### Post by TheWizzard on 2006-10-20
ok, that's clear.
my 'default' is with some additional repos.
cheers

---

### Post by mikeymikec on 2006-10-24
TheWizzard:  if you could let me know of a repository that includes recent OpenOffice releases, I'd like to know :)

---

### Post by TheWizzard on 2006-10-25
> **mikeymikec said:**
> TheWizzard:  if you could let me know of a repository that includes recent OpenOffice releases, I'd like to know :)

dapper-proposed, but from what i read packages in this repo can break your system. see [http://www.ubuntuforums.org/archive/index.php/t-246641.html](http://www.ubuntuforums.org/archive/index.php/t-246641.html)

in the end i think new versions of open office should appear in the backports repo. but i'm not sure of this. unfortunately i can't find a good repo's guide in the wiki's. :-k

---

