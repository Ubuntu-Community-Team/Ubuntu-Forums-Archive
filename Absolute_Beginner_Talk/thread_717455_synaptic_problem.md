---
title: "synaptic problem"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by zombier on 2008-03-07
Hey everyone! I am a complete noob to ubuntu so try to bear with me. I just bought an eee pc today and installed eeexubuntu. I tryed following directions to install zsnes from this site [http://linuxgamingtoday.wordpress.com/2008/01/26/how-to-install-emulators-on-ubuntu-snes-edition/](http://linuxgamingtoday.wordpress.com/2008/01/26/how-to-install-emulators-on-ubuntu-snes-edition/)  and it didnt work. Now when i try to go into synaptic i get this error..

E: Type '“deb' is not known on line 74 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Im totally clueless how to fix this. I know i shouldnt have tried this without learning more about ubuntu. So if someone can help me it would be greatly appreciated

---

### Post by Crafty Kisses on 2008-03-07
You'd do the following:
```
sudo gedit /etc/apt/sources.list
```
Go to line 74, and take that line out, or fix the error.

---

### Post by kellemes on 2008-03-07
> **zombier said:**
> Hey everyone! I am a complete noob to ubuntu so try to bear with me. I just bought an eee pc today and installed eeexubuntu. I tryed following directions to install zsnes from this site [http://linuxgamingtoday.wordpress.com/2008/01/26/how-to-install-emulators-on-ubuntu-snes-edition/](http://linuxgamingtoday.wordpress.com/2008/01/26/how-to-install-emulators-on-ubuntu-snes-edition/)  and it didnt work. Now when i try to go into synaptic i get this error..

E: Type '“deb' is not known on line 74 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Im totally clueless how to fix this. I know i shouldnt have tried this without learning more about ubuntu. So if someone can help me it would be greatly appreciated

Well, you better post the hole contents of /etc/apt/sources.list..
So we can see what's the problem..

---

### Post by zombier on 2008-03-07
hey i tryed that but got the following

alex@alex-laptop:~$ sudo gedit /etc/apt/sources.list
[sudo] password for alex:
sudo: gedit: command not found
alex@alex-laptop:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
alex@alex-laptop:~$

---

### Post by kellemes on 2008-03-07
> **zombier said:**
> hey i tryed that but got the following

alex@alex-laptop:~$ sudo gedit /etc/apt/sources.list
[sudo] password for alex:
sudo: gedit: command not found
alex@alex-laptop:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
alex@alex-laptop:~$


ok, so gedit is not installed I guess.. strange..
Are you sure you're on Ubuntu instead of Kubuntu?

How does the following respond?
```
sudo kate /etc/apt/sources.list
```

---

### Post by MONODA on 2008-03-07
try 
> sudo nano /etc/apt/sources.list
it should work.

---

### Post by zombier on 2008-03-07
> **kellemes said:**
> ok, so gedit is not installed I guess.. strange..
Are you sure you're on Ubuntu instead of Kubuntu?

How does the following respond?
```
sudo kate /etc/apt/sources.list
```

that doesnt work either

im using eeeXubuntu

---

### Post by spiderbatdad on 2008-03-07
nano would work.

---

### Post by MONODA on 2008-03-07
> 
ok, so gedit is not installed I guess.. strange..
Are you sure you're on Ubuntu instead of Kubuntu?

How does the following respond?
Code:

sudo kate /etc/apt/sources.list


@kellemes and OP: never run graphical apps with sudo, that is what gksu is for.

---

### Post by zombier on 2008-03-07
> **MONODA said:**
> try 

it should work.


that worked, but now what do i do? sorry i know im a complete noob

---

### Post by MONODA on 2008-03-07
> 
Quote:
Originally Posted by kellemes View Post
ok, so gedit is not installed I guess.. strange..
Are you sure you're on Ubuntu instead of Kubuntu?

How does the following respond?
Code:

sudo kate /etc/apt/sources.list

that doesnt work either

im using eeeXubuntu
ok then try:
> sudo mousepad /etc/apt/sources.list

---

### Post by spiderbatdad on 2008-03-07
you can install gedit on xubuntu

---

### Post by zombier on 2008-03-07
something came up with the sudo nano but i dont know what to do now

---

### Post by spiderbatdad on 2008-03-07
nano should have a little guide for you on the screen...ctrl-o to write the changes...ctrl-x to exit. you could copy and paste the contents here for us to see

---

### Post by MONODA on 2008-03-07
ok now select all the text there and just paste it in a new post in here.

---

### Post by zombier on 2008-03-07
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main r$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
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

---

### Post by spiderbatdad on 2008-03-07
your sources are mostly commented out...see this: [http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)
but of course you'll be using nano

---

### Post by MONODA on 2008-03-07
Edit: Double Post

---

### Post by zombier on 2008-03-07
> **MONODA said:**
> Edit: Double Post

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
“deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

---

### Post by Paqman on 2008-03-07
Hi Zombier,

The file /etc/apt/sources.list defines which software repositories Synaptic will look up. If you look at the file it says that most of them have been commented out by the installer (the # at the start of the line)

Did you have no internet connection during installation? If not, that's why it's done this. It couldn't make contact with those repos, so it's marked them as not available. Now that you have an internet connection you need to uncomment the repos you want to use and hit reload in Synaptic. Then you should be fine.

Also, that last line in there is wrong. It should have no quotes, and looks to be for feisty, not gutsy.

---

### Post by zombier on 2008-03-07
thanks for the help everyone. i couldnt get anything working now, but im going to try again tomorrow. im falling asleep.

---

### Post by zombier on 2008-03-07
wait i got it! thanks for your help guys!

---

