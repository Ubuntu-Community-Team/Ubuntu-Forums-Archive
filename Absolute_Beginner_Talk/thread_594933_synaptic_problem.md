---
title: "synaptic problem"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by jureuser on 2007-10-28
Hi!
This the first time I'm using ubuntu (or any other Linux application). I have a problem with synaptic. I was writing some stuff in terminal, next thing I knew, I wasn't able to enter synaptic. I got error:

E: Type '--10:37:20--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I believe at the moment I was running the commands, the internet connection was down (I didn't notice that). When I use cat /etc/apt/sources.list.d/medibuntu.list, I get


--10:37:20-- [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
=> `gutsy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.

Can you help me with this?

---

### Post by Pumalite on 2007-10-28
sudo dpkg --configure -a
You might have to get the key for Medibuntu or install it properly:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by taurus on 2007-10-28
There is something wrong with your /etc/apt/sources.list.  Open a terminal and post the whole content of your /etc/apt/sources.list here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by jureuser on 2007-10-28
With _cat /etc/apt/sources.list_ I get:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by taurus on 2007-10-28
What happens to your /etc/apt/sources.list?

Edit it

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, commenting out the CDROM repo.  Then, remove the # in front of all the lines that begin with deb and deb-src.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Also post the output of this command here.

```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by jureuser on 2007-10-28
I did as you said!
After I wrote _sudo apt-get update_, I got

E: Type '--10:37:20--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

and after _sudo apt-get upgrade_

E: Type '--10:37:20--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Seznama virov ni mogo&#269;e brati. (translation: the list of sources can't be read).

_cat /etc/apt/sources.list.d/medibuntu.list_ returned (same as before):

--10:37:20--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `gutsy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.

---

### Post by taurus on 2007-10-28
Edit /etc/apt/sources.list.d/medibuntu.list

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and place a # in front of all the lines in there.  Save the changes and run those two commands again.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jureuser on 2007-10-28
Hey, it worked! Thanks

---

### Post by RH9R on 2007-10-29
I posted the question as to whether or not medibuntu was down over the wkend, and one user said it worked fine. 
 
When I do a sudo apt-get update, the last lines show:
 
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

This thread recommended commenting out all the lines, running:
 
sudo apt-get update
sudo apt-get upgrade
 
Then uncommenting the relevant lines and re-running those two commands. The output above is the result - no change. It seems to tell me medibuntu is down. What am I missing?

---

### Post by Crafty Kisses on 2007-10-29
> **jureuser said:**
> Hey, it worked! Thanks

Mark the thread Solved.

---

### Post by RH9R on 2007-10-29
not quite solved.

---

### Post by RH9R on 2007-10-30
I can only guess fat-fingering the command strings. I found ways to cut & paste commands, and it worked.
 
Book 'em Danno  -  case closed.
 
Thanks for your kind help, all.

---

