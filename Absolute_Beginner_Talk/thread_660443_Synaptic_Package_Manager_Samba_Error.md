---
title: "Synaptic Package Manager/ Samba Error"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by JAK4073 on 2008-01-06
Ive been Trying to download and install samba onto my system but every time I type in "sudo apt-get install samba" , it asks me for my password which i then put in. then it says 

" E: Type '0690117667' is not known on line 56 in source list /etc/apt/sources.list
" E: The list of sources could not be read."

The 0690117667 is my password which is typed correct. 

Since i thought it was a problem with my password i went and changed it to ahole45.I restarted the computer and tried to install samba again and it gave me the exact same message saying my old password is not known( even after i changed it. 

Then i noticed that when i tried to open synaptic Package manager, as soon as it opens it says " an error occured" the same message as when i tried to install samba.

" E: Type '0690117667' is not known on line 56 in source list /etc/apt/sources.list
" E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report

Does anyone know what this means??

---

### Post by taurus on 2008-01-06
There is something wrong with line 56 in your /etc/apt/sources.list.  So, you need to fix it or just post it here and we'll see what's wrong with it.

```
cat /etc/apt/sources.list
```

---

### Post by JAK4073 on 2008-01-06
> **taurus said:**
> There is something wrong with line 56 in your /etc/apt/sources.list.  So, you need to fix it or just post it here and we'll see what's wrong with it.

```
cat /etc/apt/sources.list
```
[B]
I got this [/B]

jeremy@JAK-LINUX:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
0690117667
wget [http://www.getautomatix.cm/keys/automatix2.key](http://www.getautomatix.cm/keys/automatix2.key)
gpg --import automatix2.key
gpg --export --armor E23C5FC3
sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2
jeremy@JAK-LINUX:~$

---

### Post by taurus on 2008-01-06
Why are these lines in there, at the bottom of the file?

> 
0690117667
wget [http://www.getautomatix.cm/keys/automatix2.key](http://www.getautomatix.cm/keys/automatix2.key)
gpg --import automatix2.key
gpg --export --armor E23C5FC3
sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2

And any reason why you want to install automatix?  So, if you want to get your system back to normal again, you need to edit it

```
gksudo gedit /etc/apt/sources.list
```
and remove those lines from it.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by JAK4073 on 2008-01-06
> **taurus said:**
> Why are these lines in there, at the bottom of the file?


And any reason why you want to install automatix?  So, if you want to get your system back to normal again, you need to edit it

```
gksudo gedit /etc/apt/sources.list
```
and remove those lines from it.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

Thanks alot. Really appreciate it. That solved the problem, but could you explain to me what i just done and how it fixed the problem.

---

