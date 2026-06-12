---
title: "[SOLVED] add/ remove applications"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by shahriar86 on 2007-11-07
I have used windows since I was 10. I just switched to Gutsy Gibbon and the ride is not all too pleasing. The problems I am facing are taking away all the fun of using free OS.

The 1st problem is I am getting &#8220; H.V. Frequency Over Range&#8221; warning every time I boot or shutdown. I have found the solution in one of the forum posts, I need to use start-up manager to configure my boot up sequence.

Unfortunately there comes my 2nd problem. I can not use Add/Remove Applications to add any I mean any applications. the first windows appears says

&#8220;The list of applications is not available click on 'Reload' to load it.
To Reload you need working internet connection.&#8221;

I press 'Refresh' And voila comes the second window
&#8220;Downloading package information
downloading file 6 of 6
download rate unknown&#8221;

Then comes the 
&#8220;Checking installed and available applications&#8221;

and still I can not add any applications. the process just repeats itself.

The 3rd problem I am facing is Firfox is crashing every few minutes. And it has crashed 10 times already while writing this post. (I guess its not problem of Gutsy Gibbon I may report it to mozilla corp)

The 4th problem is not finding any nVidia GeForce FX driver for my Palit nVidia GeForce FX 5200 128MB graphics card. So I can not test the visual effects.

Please anybody there with the solutions help me out or I may have to switch to xp again (which I really dont want to do).

PS: I can remove applications

---

### Post by jolger on 2007-11-07
Removed

---

### Post by shahriar86 on 2007-11-07
yes I have also tried sudo apt-get install (Application Name) before posting
but it gives me following error

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package** (application Name)** has no installation candidate"

And also..
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package (Application name)


BTW: thanks for your replies.

---

### Post by taurus on 2007-11-07
What package are you trying to install?

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by JamesT1139 on 2007-11-07
I'm having the same problems. I've been trying to figure everything the past few hours. When I first installed Ubuntu 7.10 everything went fine. I then tried to connect to Pidgin-no luck with that, So I did what I always do and googled it. Well google brought back a few results, Only problem is when I clicked the links it would never load. I was running wireless at the time, so I  switched to wired. Everything was working fine. Well a few hours later I've got the wireless problem solved, regarding the pages not loading. But now Pidgin still won't connect, So I decided to remove it and then reinstall, only now I'm getting the same problem as above. It keeps telling me its out of date,

---

### Post by shahriar86 on 2007-11-07
> **taurus said:**
> What package are you trying to install?

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

**"Start-up manager"** to fix "H.V. Frequency over range" problem

and other files like 7zip or opera...

here is my /etc/apt/sources.list


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Maestro23 on 2007-11-07
> **shahriar86 said:**
> **"Start-up manager"** to fix "H.V. Frequency over range" problem

and other files like 7zip or opera...

here is my /etc/apt/sources.list


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

All your sources are commented out.(#)  Need to remove the # from all the lines that begin with deb and deb-src.  Put one in front of the line up at the top for the cd-rom source. 

Edit the file with gedit.

> gksudo gedit /etc/apt/sources.list

Then run:

sudo apt-get update

---

### Post by taurus on 2007-11-07
I don't feel like typing the whole thing over again so look at post #4 in this thread, [http://ubuntuforums.org/showthread.php?t=605665](http://ubuntuforums.org/showthread.php?t=605665).

---

### Post by shahriar86 on 2007-11-07
thanks its working now

cheers

---

### Post by Maestro23 on 2007-11-07
> **shahriar86 said:**
> thanks its working now

cheers

Good deal, please mark this SOLVED using the Thread Tools.

Thanks.:)

---

