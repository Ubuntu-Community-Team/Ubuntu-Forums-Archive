---
title: "Installing programs help..."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-25
I'm a noob at installing. 

I want to install:

aMSN
Firestarter 

I saw them on the Add/Remove under applications.. clicked on it. 
It said:

The list of applications is not available
```

Click on 'Reload' to load it. To reload the list you need a working Internet connection
```

I click the refresh button:

Something happens, cant explain it. Then I don't see the program I want.

What do I do?

Thanks,
Tom

---

### Post by Cypher on 2008-02-25
Open a terminal by Applicstions->Accessories->Terminal and type
```

sudo apt-get install amsn firestarter

```
Put your password in when prompted and it will install. If it doesn't, you may want to check on your Internet connection with
```

ipconfig -a

```
Also, if you haven't done this before, it's a good idea to update your repository view by
```

sudo apt-get update

```

---

### Post by ExpatPaul on 2008-02-25
In the top right of the Add/Remove window is a Drop down labeled Show.

Select 'All available applications' and search again. I've just tried it and did find aMSN

---

### Post by Tom--d on 2008-02-25
```
tom@Laptop:~$ sudo apt-get install amsn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amsn

```

?

---

### Post by jan quark on 2008-02-25
> Put your password in when prompted and it will install. If it doesn't, you may want to check on your Internet connection with
Code:

ipconfig -a



you mean 

```
ifconfig -a 
```
or? :)

---

### Post by Tom--d on 2008-02-25
> **ExpatPaul said:**
> In the top right of the Add/Remove window is a Drop down labeled Show.

Select 'All available applications' and search again. I've just tried it and did find aMSN

Thats what I did but It never installed :\

Also Ive got AVG installed.. is there any point in having it? and how do I uninstall it?

---

### Post by jan quark on 2008-02-25
Tom--d

please post the output of this terminal command
```

cat /etc/apt/sources.list
```

---

### Post by Tom--d on 2008-02-25
```
tom@Laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

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
tom@Laptop:~$ 

```

Erm.. is there a problem??

---

### Post by jan quark on 2008-02-25
the classic problem :)

go to system > administration > software sources

enable all sources except the source code and the cd

then run

```
sudo apt-get update
```

and try to install the application one more time

---

### Post by Tom--d on 2008-02-25
Ah thanks :D
It works!!!

O and 2 questions..

Do I need AVG?
and
I need a good music player. a simple one but with a nice GUI, anything available?

---

### Post by Cypher on 2008-02-25
No you don't need AVG and as far as Music Players go, there's XMMS, Amarok..and many more..:)

---

### Post by Cypher on 2008-02-25
> **jan quark said:**
> you mean 

```
ifconfig -a 
```
or? :)
Heh, you're right..too much going back and forth on Windows<->Linux..;)

---

### Post by kaiju on 2008-02-25
> **Tom--d said:**
> Also Ive got AVG installed.. is there any point in having it? and how do I uninstall it?

unless you want to do virus checks on drives used with windows, there's probably no reason why you would need avg.

synaptic is a great tool for adding/removing software. you'll find it somewhere under system i think, called 'synaptic package manager'. or you can start it from the 'run' box (alt+f2), by typing 'gksu synaptic'. synaptic has a search function, and a right click on the app's line will tell you more about the available options.

---

### Post by Tom--d on 2008-02-25
How do I uninstall AVG?

---

### Post by jan quark on 2008-02-25
> Heh, you're right..too much going back and forth on Windows<->Linux..

yea it can be confusing sometimes,
but it gets better when you trash windows :lolflag:

Tom--d
amarok seems best for you

although there are many more options in the open source world

---

### Post by Tom--d on 2008-02-25
Just downloading Amarok..


I must admit.. 

Ubuntu beats all the windows put together :D For me that is! Its just so nice!

---

### Post by Tom--d on 2008-02-25
Amarok is just what I was looking for!!!!! :D

Also.. how do I uninstall AVG >.< :P

---

