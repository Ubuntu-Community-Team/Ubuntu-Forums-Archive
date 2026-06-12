---
title: "Failing to connect to update repositories"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by measdg on 2006-07-30
I wasn't getting any luck here:
[http://www.ubuntuforums.org/showthread.php?t=225740](http://www.ubuntuforums.org/showthread.php?t=225740)

So i'll try in the beginners forum.

Basically; none of the system updating tools are working for me. I have a new install of Dapper from the CD, and have got internet working okay but none of the methods for updating the system are working.
I have tried: sudo apt-get update; sudo aptitude update; the Synaptic Package Manager, and the Update Manager. All of these methods fail to download the repository indexes (they time out).

For example:

measdgGLEN-NB01:/etc/apt$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done


I am connected to the internet now, so there doesn't seem to be any problem there, but these tools just don't seem to be able to access the indexes. Any ideas how to resolve this? I haven't been able to find any help in any existing threads so far.

I am familiar with linux as a user, but new to setting it up from scratch so please keep that in mind with any help

thnx

---

### Post by confused57 on 2006-07-30
Did you install the Automatix gpg keys(see key import section)?:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

Just tried, the Automatix repository is online & working OK for me.

---

### Post by measdg on 2006-07-30
I was having issues prior to trying to use automatix.
I have now gone back to a 'clean' sources.list file (without automatix) and I am still having the problem.
I am sure the repositories are ok, it is just that I am unable to connect to them.
Here is my sources.list:

measdg@GLEN-NB01:/etc/apt$ more sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by measdg on 2006-07-30
I have tried LOTS of tips + ideas from these forums, but still no luck.

My problem is very simmilar to this:
[http://www.ubuntuforums.org/showthread.php?t=188425](http://www.ubuntuforums.org/showthread.php?t=188425)

But none of the ideas have helped.

I have tried:
1) removing the proxy line in the /etc/apt/apt.conf file
2) changing the http references to ftp in the sources.list file 
3) I have successfully pinged the servers I am trying to update from, but still can't connect
4) changing the country code of the update servers 
5) checked the nameserver setting in /etc/resolv.conf

I am doing all thes from a FRESH Ubuntu install from the CD. I have not changed any of the networkin/proxy settings at all. I have not installed any new packages or anything.

ANy ideas anyone??

---

### Post by measdg on 2006-07-30
PROBLEM SOLVED.

I am not sure why, but going to the package repositories in Mozilla Firefox (e.g. [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) ) manually, changed something (i don't know what) which now allows Synaptic/apt-get etc to work.

---

