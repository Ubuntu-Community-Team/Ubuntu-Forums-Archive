---
title: "sudo apt-get update hangs"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Matymoo on 2007-10-27
[I]maty@maty-desktop:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_AU
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)][/I]

Any ideas??? I can browse internet ok... but seems I cannot update! this occurs using sudo apt-get update or when trying to use the update manager....get the following message...

[I]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/I]

---

### Post by Halfling Rogue on 2007-10-27
Hm. You checked the repository addresses? I vaguely remember having this problem back when I first installed Dapper, and I think it was because I had the wrong universes turned on, but I can't remember exactly. Can you ping archive.ubuntu.com?

---

### Post by taurus on 2007-10-27
```

taurus@taurus:~$ ping -c 3 archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=45 time=130 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=2 ttl=45 time=130 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=3 ttl=45 time=131 ms

--- archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 130.448/130.892/131.722/0.587 ms

```

---

### Post by Matymoo on 2007-10-27
> maty@maty-desktop:~$ ping -c 10 archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.46) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=1 ttl=50 time=341 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=2 ttl=50 time=342 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=3 ttl=50 time=339 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=4 ttl=50 time=340 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=5 ttl=50 time=338 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=6 ttl=50 time=337 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=7 ttl=50 time=337 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=8 ttl=50 time=339 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=9 ttl=50 time=338 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=10 ttl=50 time=340 ms

--- archive.ubuntu.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9000ms
rtt min/avg/max/mdev = 337.128/339.606/342.667/1.672 ms
maty@maty-desktop:~$ 


no probs it seems

---

### Post by Matymoo on 2007-10-27
arrrgh. Nothing seems to work in Gutsy!!!! Just tried to install the flash plugin for firefox... get a "not found" message. 

edgy worked 100%
Feisty.... nvidia problem.
Gutsy.... can't update anything.

Aren't things supposed to get better with new versions!! :mad:

---

### Post by taurus on 2007-10-27
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Matymoo on 2007-10-27
.....
> maty@maty-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse #Added by software-properties
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main universe restricted multiverse #Added by software-properties
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main universe restricted multiverse #Added by software-properties

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main universe restricted multiverse #Added by software-properties
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
maty@maty-desktop:~$ 



---

### Post by Matymoo on 2007-10-27
....and then????

---

### Post by Matymoo on 2007-10-28
Ok. That's it

I give up.

I am so pi$$ed off. I will revert back to a stable version of ubuntu.... Feisty.

Gutsy is a pile of *****!!!!! I have tried for 2 weeks to sort out these problems. No fix I have followed seems to work.

I am extremely disappointed as I really like using ubuntu and think it is a major step backwards having to use Feisty.

Let's hope that the next release is FIXED.

---

### Post by PippoFranco on 2007-10-28
I had similar problems. In the last weeks I made several attempts to install Gutsy on my two laptops (Acer TravelMate 370 and 8200) which work now with Feisty.

The live CD doesn't recognize properly my hardware (I had no problem with Feisty). Networking works only if I disable Ipv6.

Installation hangs during the apt set up and kills the sources.list file, doesn't handle languages other than English, on the installed system synaptic doesn't work (with a new sources.list).

From the long list of forum entries on similar style I can assume that I am not the only person in trouble.

For the time being I stick with Feisty

Suggestions on how to fix apt?

--f

---

### Post by Matymoo on 2007-10-28
I am actually going to give PCLinuxOS a go. Ubuntu had me for almost a year. Too bad Gutsy finished that.

---

### Post by Matymoo on 2007-10-29
OpenSUSE 10.3 won in the end.

---

### Post by Matymoo on 2007-11-02
Update.....

OpenSUSE has been running perfectly, BUT.... stumbled across the possible cause of my Gutsy woes by accident! Seems it could possibly be my DSL-G604T router.

Have updated firmware as per threads here.... just downloading gutsy CD again as I lost it.

If this works, I will will return to Ubuntu for the simple fact that the support available through these forums is far better than what is available for openSUSE.

Still, why is it that both PClinuxOS and OpenSUSE had no trouble with the older firmware..... but Gutsy doesn't like it? :confused:

---

### Post by Matymoo on 2007-11-03
Well, Gutsy is back on my PC. This time, with my newly firmware updated DSL-G604T.

No need to turn off IPV6!

apt-get update worked 100% 

system updates, 100%!

Nvidia driver installed without a hitch.

Smoothest Ubuntu install yet!

If you are having probs like I did, and you have a DSL-G604T router, go to the dlink website for your region and get the latest firmware! It fixed ALL my gutsy problems.

Like I said in the previous post.... WHY is it that this affects gutsy only? Other distros I have used worked fine.....

---

### Post by jaybombalous on 2007-11-03
Its probably because ipv6 is default in the ubuntu kernel. Thats just a guess though.


glad u came back to ubuntu, gutsy is really a good OS, but like anything new u gotta work the kinks out.

---

