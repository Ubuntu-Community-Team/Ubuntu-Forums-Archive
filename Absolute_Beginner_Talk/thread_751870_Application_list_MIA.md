---
title: "Application list MIA"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Rubby on 2008-04-11
First off, let me say that I searched, and I RTFM'd. So above all else, The least I can say is that I tried.
whenever I attempt to get any application to install. it just won't... let me guide you through my interest provoking steps which displays my problem
*attempt to open mp-3 file, movie player opens, and kindly informs me that the codecs is not supported due to the lack of a decoder*
*asks if it would like me to search for a suitable codecs, i select "yes"*
*the codecs screen pops up and i select a suitable codecs*
*I double clicky, it asks me to confirm I'll be using it for legal reasons, then it tells me the list is not "availabe" (sp?)*
* a clicky of refresh brings me back up 3 steps*
and from there it repeats, help?
This is the same for all my applications in the "Add/Remove Applications" application(?))
Hope you guys can help, cheers

---

### Post by FuturePilot on 2008-04-11
Could you post your sources.list?
```
cat /etc/apt/sources.list
```
Post the output of that command.

---

### Post by Rubby on 2008-04-11
> **FuturePilot said:**
> Could you post your sources.list?
```
cat /etc/apt/sources.list
```
Post the output of that command.
ask and you will receive sauce
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by FuturePilot on 2008-04-11
Wow! The entire thing is commented out :shock: lol
To fix it
```
gksudo gedit /etc/apt/sources.list
```
Remove the # sign in front of all the lines beginning with "deb" and "deb-src"
Also add a # sign to the very first line that begins with "deb cdrom:"
Once you have done that save it and run
```
sudo apt-get update
```
to update the sources. That should fix your problem :)

---

### Post by Rubby on 2008-04-11
> **FuturePilot said:**
> Wow! The entire thing is commented out :shock: lol
To fix it
```
gksudo gedit /etc/apt/sources.list
```
Remove the # sign in front of all the lines beginning with "deb" and "deb-src"
Also add a # sign to the very first line that begins with "deb cdrom:"
Once you have done that save it and run
```
sudo apt-get update
```
to update the sources. That should fix your problem :)
aa soo desu ka.
Anyway, Thanks a bunch... I figured the entire thing commented out seemed rather odd...
Thanks again FuturePilot

---

### Post by FuturePilot on 2008-04-11
No problem :)

---

