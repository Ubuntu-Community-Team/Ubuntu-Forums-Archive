---
title: "Couldn't find package ksh"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by sahana on 2007-11-22
Hi

I just installed Ubuntu 7.10 and I am installing additional packages needed to install Oracle on it. But whatever I try, I get the "Could not find package" error.
Here is an example:

root@naru-desktop:~# apt-get install ksh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ksh

When I try rpm:

root@naru-desktop:~# apt-get install rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rpm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rpm has no installation candidate

Here is what I get when I upgrade:

root@naru-desktop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Can some please help?

Thanks in advance

---

### Post by taurus on 2007-11-22
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by sahana on 2007-11-22
Thanks for the quick response. There are many lines with # at the beginning of the line. So I did: cat /etc/apt/sources.list|grep -v '^#'


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
root@naru-desktop:~# 

Thanks again

---

### Post by taurus on 2007-11-22
Can you post the whole thing?  I think you have a bunch of repos comment out, with a # in front of them, so apt-get can't find anything.  Therefore, you need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all the lines that start with **deb** & **deb-src**.  Then, save it and close gedit.  

Now, run

```
sudo apt-get update
sudo apt-get install ksh
```

---

### Post by sahana on 2007-11-22
Full cat:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by sahana on 2007-11-22
Hi Taurus,

I have just posted the full list. Should I uncomment all deb and deb-src lines? 

Thanks again

---

### Post by taurus on 2007-11-22
Yes.  Just read over my previous post.  However, you may want to comment out the first line, cdrom, by placing a # in front of it so it stops asking you to insert a CD into a drive.  Kind of annoying after a while.  Have the system install everything from the net.

---

### Post by sahana on 2007-11-22
Hi Taurus,

That seemed to have get past my problem. However I am still not able to run the update. Here is what happens:

root@naru-desktop:/etc/apt# sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_AU           
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_AU               
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out


However, I am able to ping the ip addresses:

naru@naru-desktop:~$ ping 91.189.90.142
PING 91.189.90.142 (91.189.90.142) 56(84) bytes of data.
64 bytes from 91.189.90.142: icmp_seq=1 ttl=40 time=358 ms
64 bytes from 91.189.90.142: icmp_seq=2 ttl=40 time=358 ms
64 bytes from 91.189.90.142: icmp_seq=3 ttl=40 time=358 ms
64 bytes from 91.189.90.142: icmp_seq=4 ttl=40 time=358 ms

similar thing happens (it seems to hang) when I use the update manager gui. 

Is it using the wrong port? Seems a setup thing

Thanks again

---

### Post by sahana on 2007-11-23
Hi,

I can get the update manager working after setting the proxy address and port in synaptic package manager settings.

But I still cannot get apt-get working. My proxy address is 172.17.72.58 and port 8080. I created a file apt.conf in /etc/apt with the line

Acquire::http::Proxy "172.17.72.58";

But it is still timing out presumable because the port is wrong.

If I change it to 

Acquire::http::Proxy "172.17.72.58:8080"

root@naru-desktop:/etc/apt# apt-get install ksh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ksh
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1127kB of archives.
After unpacking 2322kB of additional disk space will be used.
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe ksh 93r-1ubuntu1
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/k/ksh/ksh_93r-1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/k/ksh/ksh_93r-1ubuntu1_i386.deb)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Thanks in advance

---

### Post by sahana on 2007-11-23
Everything is ok now. I missed the http:// bit in apt-conf

---

