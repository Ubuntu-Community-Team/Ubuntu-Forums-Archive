---
title: "cant install programs"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by irunwithknives on 2008-02-06
neither terminal or add remove programs will allow me to install new apps.  I have other problems, but this is the most troubling one.

When I try to check an item in Add/remove programs, it gives me a message that tells me "The list of applications is not available
Click on 'Reload' to load it. To reload the list you need a working internet connection."
and I have working internet.

The sudo command in terminal always goes through the whole enchilada, and then it screws me over by saying it cant find suchandsuch file.

Also, i cant install internet plugins like the flash player and stuff.

---

### Post by twiceasworn on 2008-02-06
Are you receiving errors when you try to install?  If so what are they?

---

### Post by ptn107 on 2008-02-06
You need to be more specific, post some terminal output or errors.

---

### Post by PeterJS on 2008-02-06
What error are you getting? The terminal is generally better for getting verbose error messages.

---

### Post by petersonjacob on 2008-02-06
try
sudo apt-get update
then retry installing the program

if this doesnt work and you are trying to install a program thats compatible with windows try this:
sudo apt-get install wine

otherwise try reinstall ubuntu, i have messed up a multitude of times and had to reinstall, just give it time

---

### Post by jan quark on 2008-02-06
usually the problem are the sources

post the result of 
```

cat /etc/apt/sources.list
```

---

### Post by irunwithknives on 2008-02-06
> **jan quark said:**
> usually the problem are the sources

post the result of 
```

cat /etc/apt/sources.list
```

```

irunwithknives@sh:~$ cat /etc/apt/sources.list
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

### Post by nikoPSK on 2008-02-06
enable your repos from System -> Administration -> Software Sources. :)

---

### Post by irunwithknives on 2008-02-06
> **nikoPSK said:**
> enable your repos from System -> Administration -> Software Sources. :)

I am like really new to linux, so I dont know exactly what I am enabling-
please specify?

---

### Post by nikoPSK on 2008-02-07
> **irunwithknives said:**
> I am like really new to linux, so I dont know exactly what I am enabling-
please specify?

more software. The name should explian. I think almost everyone has all repos enabled. :) This should explain more:
[http://ubuntuforums.org/showthread.php?t=644478](http://ubuntuforums.org/showthread.php?t=644478)

nikoPSK

---

### Post by jan quark on 2008-02-07
thats right you cant download software without the source to it

all your sources in the sources.list are commented out , they are inactive enable them as mentioned above and everything should be fine

---

