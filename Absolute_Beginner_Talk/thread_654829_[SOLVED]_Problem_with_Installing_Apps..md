---
title: "[SOLVED] Problem with Installing Apps."
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2007-12-31
Ok, so I finally got everything square in Ubuntu. However, I am unable to download and install select apps. I am using the add/remove manager and on several packages I am getting the following error messages: 

"Cannot Install "insert app name" This application conflicts with installed software."

"insert app name" cannot be installed on your computer type (i386)

I get this for a crazy amount of applications. So, I am thinking that there is something wrong. I would really like to play Armagetron lol. Anyways, if anyone could help me that would be awesome :)

---

### Post by Cypher on 2007-12-31
Try the command line and perhaps we'll get more information/errors..so Applications->Accessories->Terminal and then type
```

sudo apt-get install armagetron

```
When prompted, enter your password and it will either install the package or fail. If it fails, cut-n-paste the errors..

---

### Post by skaldicpoet9 on 2007-12-31
> **Cypher said:**
> Try the command line and perhaps we'll get more information/errors..so Applications->Accessories->Terminal and then type
```

sudo apt-get install armagetron

```
When prompted, enter your password and it will either install the package or fail. If it fails, cut-n-paste the errors..

Here is what I get:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
armagetron: Depends: armagetronad but it is not going to be installed
E: Broken packages


I got this "broken packages" error before when I was trying to enable my graphics card driver. Someone gave me a cmd line for repairing broken packages but apparently it didn't work or maybe I typed it wrong? I don't know.

---

### Post by skaldicpoet9 on 2007-12-31
btw...I get this same thing with a lot of other programs as well. So I don't think that it is just a issue for a particular piece of software.

---

### Post by skaldicpoet9 on 2008-01-01
Can anyone help me with this?

---

### Post by taurus on 2008-01-01
Can you post your /etc/apt/sources.list?  Bet most (if not all) of the repos are comment out in there.

```
cat /etc/apt/sources.list
```

---

### Post by skaldicpoet9 on 2008-01-01
Here it is:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by taurus on 2008-01-01
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it and.  Then remove the # in front of all the lines that start with **deb** & **deb-src**.  Save the changes and close down gedit window.  

Now, see if you can install the program that you wanted before.

```
sudo apt-get update
sudo apt-get install armagetron
```

---

### Post by skaldicpoet9 on 2008-01-01
Awesome! 

That worked like a charm.

Now, exactly what did I do and what was the problem?

---

### Post by reefsrt4 on 2008-01-01
All of your sources were commented out via the "#".

---

### Post by taurus on 2008-01-01
> **skaldicpoet9 said:**
> Awesome! 

That worked like a charm.

Now, exactly what did I do and what was the problem?

Probably when you installed Gutsy, there was a problem with your network connection so the installer couldn't verify those repos.  Instead of probing, taking forever, the installer decided to move on to finish the job, commenting out the repos in your /etc/apt/sources.list except the CDROM.

---

### Post by Gone fishing on 2008-01-01
# commented out means, ignore this without # in front of the cdrom entry it meant that Ubuntu needed to look at the cdrom before it could install any software removing the # told Ubuntu to look at this source as a place to install software from.

---

### Post by skaldicpoet9 on 2008-01-01
Oh ok, I remember during install it said something to the effect of "Ubuntu cannot install some security updates" or something like that. Anyways, thanks a lot for the help :)

---

