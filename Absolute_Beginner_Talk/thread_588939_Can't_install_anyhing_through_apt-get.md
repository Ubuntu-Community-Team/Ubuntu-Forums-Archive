---
title: "Can't install anyhing through apt-get"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-10-23
When ever I go to add or remove and click on something to be installed it says 
"The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. "

So I click on "Refresh" and the it says

"Downloading package informaition
The repositories will be checked for new, removed or upgraded software packages."

But then every time I click on something to download it does the same thing.

I just now installed Ubuntu 7.10 by the way.

---

### Post by Dr Small on 2007-10-23
Have you tried installing anything from the command line, or Synatpic ?
Preferably, try the command line, and install something, so we can see the ouput of the errors, if there are any.

Dr Small

---

### Post by microsoft92sucks on 2007-10-23
```
spaje@EggHead:~$ sudo apt-get install abuse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package abuse
```

```

spaje@EggHead:~$ sudo apt-get install azureus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package azureus
```

It appears it can't find the packages...
Any Idea's on what to do?

---

### Post by Maestro23 on 2007-10-23
Post your sources.list

> cat /etc/apt/sources.list

---

### Post by Dr Small on 2007-10-23
Sounds like you need to enable universe repositories.

---

### Post by microsoft92sucks on 2007-10-23
```
spaje@EggHead:~$ cat /etc/apt/sources.list 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

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

### Post by Maestro23 on 2007-10-23
Go into: System>> Admin>> Software Sources

Enable your repos, everything is commented out in your sources.list

*What were you doing to have everything in your sources.list commented out.  No wonder you system can find anything.

---

### Post by microsoft92sucks on 2007-10-23
> **Dr Small said:**
> Sounds like you need to enable universe repositories.

Never had to do it for Ubuntu before. But how do I do it?

---

### Post by Dr Small on 2007-10-23
O.o
> # Line commented out by installer because it failed to verify

That leaves you with no repositories!
Why in the world!?

Maybe you could try uncommenting them...

---

### Post by microsoft92sucks on 2007-10-23
I got it working I don't know what was up with it. But all I had to do was enable all that stuff through System>> Admin>> Software Sources like Maestro23 said.
Thanks for all the help.

---

### Post by Dr Small on 2007-10-23
Please remember to mark your thread as solved from Thread Tools!

---

### Post by Maestro23 on 2007-10-23
> **microsoft92sucks said:**
> I got it working I don't know what was up with it. But all I had to do was enable all that stuff through System>> Admin>> Software Sources like Maestro23 said.
Thanks for all the help.

Good deal.  Pleas mark this thread SOLVED using the Thread Tools.

Thanks.:)

---

### Post by Hobbs131 on 2007-10-23
i'm having this problem also...im going to try the solutions provided but if it doesnt work ill repost another thread. thanks guys

---

### Post by leexgx on 2007-10-23
with ubuntu gusty 7.10 make sure internet is unpluged before installing (if upgrade realy make sure the cable not pluged in or it mite brake it)

if upgradeing or frash install or have all ready installed make sure you have done this After install (ignore the source error you get when installing)

goto System > Admin > software sources

1 Tick all boxs apart form source code (do not think norm users need that)
2 Pick your Download From server location (as it picks main server by default click on search if you cant see one for you)
3 Goto updates and tick the first 2 options
4 [Optional] change the auto up date check to [Download all updates in background] (asmuing you do not have an hard disk that is very small its an better option so your ready to install when you are ready just means you do not need to have to wait for them to download)
do not recommend auto install with out confirmation as it may not wait for all updates to be install when shuting down the pc, as it make brake your box

---

