---
title: "What am I doing wrong ? gdebi !"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by scopo on 2008-01-01
Hi all,

I am trying to install IPBLOCK.

However, gdebi keeps stating that...
**"Dependency is not satisfiable:  Libnfnetlink1 **

I have Java6 installed and I am running Gutsy so surely it should be asking for **Libnfnetlink0 **should it not ? 

Please help me understand what I am doing wrong !
Thanks

---

### Post by PmDematagoda on 2008-01-01
Could you post the results of:-
```

cat /etc/apt/sources.list
```

---

### Post by scopo on 2008-01-01
Hi thanks for your help !...

> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
 

---

### Post by skymera on 2008-01-01
take the # away fom all lines hat begin with either DEB or DEB-SRC

then try

---

### Post by PmDematagoda on 2008-01-01
Open the sources.list file for editing using:-
```
gksudo gedit /etc/apt/sources.list
```
Then remove the # in front of the repository addresses such as these:-
```
# deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates universe

# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates universe
```
to make them look like this:-
```
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy universe

deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy universe
```

After the editing is done, save the file and then execute:-
```
sudo apt-get update
```

You should then be able to install IPBlock.

---

### Post by steveneddy on 2008-01-01
Just a question.

What does this do that editing the hosts file doesn't.

Linux is already very secure, and I only wonder why you need this installed?

---

### Post by gmaniac on 2008-01-01
> **scopo said:**
> 
..
I am running Gutsy so surely it should be asking for **Libnfnetlink0 **should it not ? 


You probably downloaded the feisty package by mistake.

---

### Post by scopo on 2008-01-01
Hi, thanks for your help everyone !

I tried all of the above and none of it appeared to help 
> 
You probably downloaded the feisty package by mistake.

How embarrassing !:redface: but this is exactly what I did !!!
Downloaded the right package and now it installed a treat !

> Just a question.

What does this do that editing the hosts file doesn't.

Linux is already very secure, and I only wonder why you need this installed?

I am still new to ubuntu and  come from the windows world so it has taken a lot of hard work to get my head around the fact that I no longer need a GUI'ed  firewall, an AV program hogging the resourses in that background and a anti-spyware program (I am still having problems trying to accept this latter one - after all its still firefox browsing the web so why cant I be subject to the same spyware ?)

But, to get to the point - I use IPBLOCK (as I used Peerguardian in windows- on which the lists of IPBLOCK are based ) in order to lessen the chance that I end up on the wanted lists of various ant-P2P organizations. 

Of course it also has the added bonus that...
- It can pick up on websites which collect a little too much information
- It often highlights when you are wasting your time downloading fake torrents as the blocked list lights up like a Christmas tree  .  
- it offers a very useful insight into which programs on your system call home a little too often - [Yes adobe and MS I am looking at you !!!] (Although granted this last point  is usually more applicable to the windows world! !

Now, do I not really need that spyware scanner ????:)

---

### Post by steveneddy on 2008-01-01
Frankly, if you use Firefox and install No Script and Flashblock, you shouldn't have any problems  with anything bad on the internet.

Linux is very secure out of the box. I don't have any of that software installed on any of my Linux machines ( server, desktop, laptop ) and have never had any problems with the things that you came to abhor in the Windows world.

Relax, and accept the fact that you don't have to be so proactive in this world. It's time to enjoy the internet for a change.

:popcorn:

---

