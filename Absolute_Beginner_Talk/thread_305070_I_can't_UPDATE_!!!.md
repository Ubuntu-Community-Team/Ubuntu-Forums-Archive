---
title: "I can't UPDATE !!! ?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Janoubie on 2006-11-22
:confused: 

i cant't update 
really and i try to install update more notes come 
i collect for someone help ](*,) 

===

E: Malformed line 1 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
===

E: Malformed line 1 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
==
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

==
Could not upgrade the system!
Fix broken packages first.

==

---

### Post by taurus on 2006-11-22
Can you display your /etc/apt/sources.list here?  Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
cat /etc/apt/sources.list
```

---

### Post by Janoubie on 2006-11-22
> **taurus said:**
> Can you display your /etc/apt/sources.list here?  Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
cat /etc/apt/sources.list
```

how to solve ???? :confused:

---

### Post by jordanmthomas on 2006-11-22
Follow Taurus's directions he has provided so he can figure out how to solve your problem.  (First, he has to know exactly what is wrong)

---

### Post by taurus on 2006-11-22
> **Janoubie said:**
> how to solve ???? :confused:
I need to see your /etc/apt/sources.list to see what's wrong with it first before I can tell you how to solve it!!!

```
cat /etc/apt/sources.list
```

---

### Post by Janoubie on 2006-11-22
frist i change this steps :!:

---

### Post by Janoubie on 2006-11-22
eton@eton-desktop:~$ cat /etc/apt/sources.list
deb None edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb None edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse main #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb None edgy-backports main restricted universe multiverse

deb None edgy-updates main restricted universe multiverse

deb None edgy-security main restricted universe multiverse

deb None edgy main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse restricted main #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse restricted main #Added by software-properties
#AUTOMATIX REPOS END

---

### Post by taurus on 2006-11-22
> **Janoubie said:**
> frist i change this steps :!:
Okay, I am only to repeat this again.  Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here!

```
cat /etc/apt/sources.list
```
You can use your left button to cut and middle or both left and right to paste...

---

### Post by taurus on 2006-11-22
> **Janoubie said:**
> eton@eton-desktop:~$ cat /etc/apt/sources.list
deb None edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb None edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse main #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb None edgy-backports main restricted universe multiverse

deb None edgy-updates main restricted universe multiverse

deb None edgy-security main restricted universe multiverse

deb None edgy main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse restricted main #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse restricted main #Added by software-properties
#AUTOMATIX REPOS END

You need to put a # in front of these two lines at the top of your /etc/apt/sources.list since they don't even make sense...

```

#deb None edgy main restricted

#deb None edgy-updates main restricted

```
You can edit it with this command.

```
gksudo gedit /etc/apt/sources.list
```
Save the changes and from a terminal, run

```
sudo aptitude update
sudo aptitude upgrade
```
p.s.  Where did you get this /etc/apt/sources.list anyway because it looks to me like you are missing a few things or some lines are off???

---

### Post by Janoubie on 2006-11-22
eton@eton-desktop:~$ sudo aptitude update
Password:
E: Malformed line 38 in source list /etc/apt/sources.list (URI parse)
E: Malformed line 38 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.

---

### Post by Janoubie on 2006-11-22
problem here :
line 38  deb None edgy-backports main restricted universe multiverse

39      deb None edgy-updates main restricted universe multiverse

40      deb None edgy-security main restricted universe multiverse

---

### Post by taurus on 2006-11-22
> **Janoubie said:**
> problem here :
line 38  deb None edgy-backports main restricted universe multiverse

39      deb None edgy-updates main restricted universe multiverse

40      deb None edgy-security main restricted universe multiverse

You need to put # in front of those lines as well...

---

### Post by Janoubie on 2006-11-22
thanks ............ 
realy i love ubuntu becouse help under touch
sloved man

---

### Post by taurus on 2006-11-22
So everything is good now!

---

### Post by arnieboy on 2006-11-22
just delete the following lines:
> deb None edgy-backports main restricted universe multiverse

deb None edgy-updates main restricted universe multiverse

deb None edgy-security main restricted universe multiverse

deb None edgy main restricted universe multiverse
and save your sources.list and then do a
```
sudo apt-get update
```
How did the word "None" come in within the AX list? did you edit your sources manually?

---

### Post by taurus on 2006-11-22
> **arnieboy said:**
> just delete the following lines:
and save your sources.list and then do a
```
sudo apt-get update
```
How did the word "None" come in within the AX list? did you edit your sources manually?
That's why I wonder where you got his original /etc/apt/sources.list because the first line got the "None" in there...

---

### Post by arnieboy on 2006-11-22
> **taurus said:**
> That's why I wonder where you got his original /etc/apt/sources.list because the first line got the "None" in there...

yeah that too..

---

### Post by glyndelacy on 2006-11-22
Strange, I am having exactly the same problem. When I started up today I had a notification on the top bar saying 'an error occurred please run package manager to see what's wrong' and when I investigated I got the following message from the terminal: 
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I checked on the sources.list and it was empty. Since then I have not been able to recover from this problem. Any ideas?

---

### Post by taurus on 2006-11-22
> **glyndelacy said:**
> Strange, I am having exactly the same problem. When I started up today I had a notification on the top bar saying 'an error occurred please run package manager to see what's wrong' and when I investigated I got the following message from the terminal: 
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I checked on the sources.list and it was empty. Since then I have not been able to recover from this problem. Any ideas?
It cannot be empty because it complains about line 38 in /etc/apt/sources.list!!!  Are you sure you looked in /etc/apt/sources.list (check the spelling)?

---

### Post by arnieboy on 2006-11-22
> **glyndelacy said:**
> Strange, I am having exactly the same problem. When I started up today I had a notification on the top bar saying 'an error occurred please run package manager to see what's wrong' and when I investigated I got the following message from the terminal: 
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I checked on the sources.list and it was empty. Since then I have not been able to recover from this problem. Any ideas?
well the sources.list could not have been empty if it had reported the error:
whats the output for 
```
cat /etc/apt/sources.list
```

---

### Post by glyndelacy on 2006-11-22
glyn@glyn-desktop:~$ sudo aptitude update
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
glyn@glyn-desktop:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) breezy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) breezy universe
deb [http://archieve.canonical.com/ubuntu](http://archieve.canonical.com/ubuntu) dapper-commercialmain
glyn@glyn-desktop:~$

---

### Post by taurus on 2006-11-22
You shouldn't mix Breezy & Dapper in Edgy so either remove the last three lines or put a # in front of them...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by arnieboy on 2006-11-22
change the last line in your sources.list to
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
and do a 
```
sudo apt-get update
```
The number 38 in this case was purely coincidential

---

### Post by arnieboy on 2006-11-22
> **taurus said:**
> You shouldn't mix Breezy & Dapper in Edgy so either remove the last three lines or put a # in front of them...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```
taurus: dapper-commercial works fine on edgy. In fact the last time I checked they hadnt moved the packages from dapper-commercial to edgy-commercial. Since they are all proprietary software with no serious dependencies, there will be no problem.

---

### Post by glyndelacy on 2006-11-22
Well Done! that's done it.
Many thanks.

---

### Post by barat on 2006-11-23
similar problem,please please help, i have no idea how to solve:-( error message is like this:
hant@desktop:~$ sudo aptitude update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.

hant@desktop:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe #Added by software-properties

---

### Post by Bachstelze on 2006-11-23
Do you have any other package management app open, like Synaptic ?

---

### Post by barat on 2006-11-23
no, i cant.whatever i tried to install gives same problem:-(

---

### Post by barat on 2006-11-23
problem solved:-)

---

### Post by Janoubie on 2006-11-23
thanks more and more .. I think there is a bug i see it i will send pics nearly ..

---

