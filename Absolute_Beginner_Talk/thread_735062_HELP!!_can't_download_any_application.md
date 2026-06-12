---
title: "HELP!! can't download any application"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by angel_zone on 2008-03-25
i was searching the web for some new application and i found that website 
([http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html](http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html))
i followed the instruction and typed the following command in the terminal
(wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - )
and then tried to install vlc player but there was something wrong with the package file i think i closed the terminal and when i tried to start the synaptic manger again i received this message 
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
also when tried to open add/remove list
(This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.)
any help please

---

### Post by quinnten83 on 2008-03-25
do the following
in a terminal type
```

sudo gedit /etc/apt/sources.list
```

remove anything having to do with medibuntu
close gedit and then type in terminal

```
sudo apt-get update
```

VLC is in the provided repos, so you don't have to install the medibuntu repositories. If not, try to get it as a .deb package at getdeb.net

---

### Post by angel_zone on 2008-03-25
((remove anything having to do with medibuntu))
i typed the command and the source list appears but sorry  i don't get it how to do that ??

---

### Post by angel_zone on 2008-03-25
this what appears 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by oedha on 2008-03-25
your repo is only to cannonical....
can you open system - administration - software sources
then mark all boxes.....
after that close....reload
then open terminal :==> applications - accessories - terminal
type :==> sudo apt-get install vlc

---

### Post by angel_zone on 2008-03-25
installing vlc is not my proplem now!!! my proplem is when i tried to start the synaptic manger or add/remove list that error message i pasted in my first post appears and i want to fix this. any help would be great

---

### Post by angel_zone on 2008-03-25
> **quinnten83 said:**
> do the following
in a terminal type
```

sudo gedit /etc/apt/sources.list
```

remove anything having to do with medibuntu
close gedit and then type in terminal

```
sudo apt-get update
```

VLC is in the provided repos, so you don't have to install the medibuntu repositories. If not, try to get it as a .deb package at getdeb.net

i posted what appears when i typed the following command
sudo gedit /etc/apt/sources.list
but i can't find any thing related to medibuntu?? so what to do then?

---

### Post by quinnten83 on 2008-03-25
ok, 
I don't know exactly what you did, but it might have something to do with the key add.
I'm affraid your going to have to wait for someone a bit more experienced to come along and help you out there.

---

### Post by Oldsoldier2003 on 2008-03-25
> **angel_zone said:**
> i posted what appears when i typed the following command
sudo gedit /etc/apt/sources.list
but i can't find any thing related to medibuntu?? so what to do then?

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
then go into Administration > Software sources and enable the first 4 repositories

now you should be able to do
```
sudo apt-get update
```to update your package lists
and ```
sudo apt-get upgrade
```to upgrade any packages that need upgrading.

what happened is you managed to enter the medibuntu repo  incorrectly and the updaters were choking on the malformed sources.list

---

### Post by quinnten83 on 2008-03-25
stoopid question, but have you tried doing what it said in the error message?

```
sudo apt-get update
```

```
sudo apt-get install -f
```?

---

### Post by oedha on 2008-03-25
what if....
open terminal type :==>
sudo apt-get install -f
then 
sudo apt-get update

---

### Post by angel_zone on 2008-03-25
> **quinnten83 said:**
> ok, 
I don't know exactly what you did, but it might have something to do with the key add.
I'm affraid your going to have to wait for someone a bit more experienced to come along and help you out there.

O.K should i change the title of the post then to NEED EXPERIENCED HELP!!!!!](*,):cry:

---

### Post by pseudo-random on 2008-03-25
Could you show us the result of 
> cat /etc/apt/sources.list.d/medibuntu.list
Your prob is in that file.
thanks

---

### Post by Oldsoldier2003 on 2008-03-25
> **quinnten83 said:**
> stoopid question, but have you tried doing what it said in the error message?

```
sudo apt-get update
```

```
sudo apt-get install -f
```?

Because the sources.list for medibuntu was fragged and in this case deleting it and starting fresh is easiest and fastest.

---

### Post by Oldsoldier2003 on 2008-03-25
> **pseudo-random said:**
> Could you show us the result of 

Your prob is in that file.
thanks

looking at the OP its clear that the repo was added using an older and now incorrect tutorial. It's faster to just delete the file and start clean.

---

### Post by northern lights on 2008-03-25
Your sources.list resides in /etc/apt/. In a subfolder, namely /etc/apt/sources.list.d/ you'll find that medibuntu.list file. Get rid of it. Either open nautilus with as root ```
gksu nautilus
```navigate to the folder and delete the file or simplyn enter
> **Oldsoldier2003 said:**
> ```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
in a terminal window.

Now for a practical sources.list:

A pound (#) in front of a line comments it - i.e. the line is for the user's convenience readable, but it will not be used by software accessing the sources.list. deb-src repositories are only relevant if you plan on modifying sources or are interested in the source code of a particular app. Given your current problems I hope I may safely assume you're not. Since you won't use the LiveCD for anything but the initial installation you can also comment the first line. Here's my suggestion of what to (un)comment in your current list:

In a terminal, again type```
gksu gedit /etc/apt/sources.list
```

Below, I've copied your sources.list
Remove all red-marked #s and add all green ones

[COLOR="Lime"]#[/COLOR]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
[COLOR="Red"]#[/COLOR] deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
[COLOR="Red"]#[/COLOR] deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
[COLOR="Red"]#[/COLOR] deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
[COLOR="Red"]#[/COLOR] deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
[COLOR="Red"]#[/COLOR] deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Theoretically you could certainly remove everything with two pounds (##), but as you seem unsure as to what is what you might wanna leave the explanations...

---

### Post by angel_zone on 2008-03-25
hi guys sorry there was a connection proplem i'll try what you said and post the results thank you for replays

---

### Post by Oldsoldier2003 on 2008-03-25
> **angel_zone said:**
> hi guys sorry there was a connection proplem i'll try what you said and post the results thank you for replays

No worries. BTW I sent a note to the owner of the howto you referenced in your OP. Hopefully the howto will be revised to avoid this problem for people in the future.

---

### Post by angel_zone on 2008-03-25
can't find that file!!!/etc/apt/source.list.d/medibuntu.list and can't delete it as it is not there????????? any ideas

---

### Post by northern lights on 2008-03-25
> **angel_zone said:**
> can't find that file!!!/etc/apt/source.list.d/medibuntu.list and can't delete it as it is not there????????? any ideas

It's source[COLOR="Red"]s[/COLOR].list ...

---

### Post by angel_zone on 2008-03-25
> **northern lights said:**
> It's source[COLOR="Red"]s[/COLOR].list ...

IT WORKS with source(S)..well thank you for helping:lolflag: i didn't realize the power of terminal and command line till now thanks again

---

