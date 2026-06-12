---
title: "Update/Add programs error"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by rokkaman on 2007-10-13
I just installed 7.10, and I cannot get an updated file list when i use Add/Remove or Update. Every time I use Add/Remove, it will say:The list of applications is not available. Click on 'Reload' to load it. To reload the list you need a working internet connection.

It will ask for the admin password. It then seems to obtain 6 packages, although this process only takes a second and no file names are shown, as if it's not connecting to the internet at all (which I am). I go to click on a program, it tells me that my file list is out of date again. :(

I've also tried sudo apt-get update and sudo apt-get upgrade, and neither seem to get any data either.

Any help would be greatly appreciated :D

---

### Post by 67GTA on 2007-10-13
What output do you get when you run > sudo apt-get update
Any error messages?

---

### Post by rsambuca on 2007-10-13
Perhaps there is a problem with your repository sources.  Can you open a terminal and post the output of 

cat /etc/apt/sources.list

---

### Post by rokkaman on 2007-10-13
> **67GTA said:**
> What output do you get when you run 
Any error messages?

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071010) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071010) gutsy/restricted Translation-en_GB
Reading package lists... Done



> **rsambuca said:**
> Perhaps there is a problem with your repository sources.  Can you open a terminal and post the output of 

cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071010)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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

---

### Post by 67GTA on 2007-10-13
You need to uncomment the repos in /etc/apt/sources.list. In a terminal run > sudo gedit  /etc/apt/sources.list

Then remove the #'s from the repos you want to use. Run > sudo apt-get update 

Depending on what you want, you might uncomment everything except the source repos. If you are just starting with Ubuntu/Linux, you probably won't use the source packages. They are labeled deb-src. Remove the cdrom entry. Are you sure you have a working internet connection?

---

### Post by por100pre1 on 2007-10-13
```
gksudo software-properties-gtk
```

Check **main**, **universe**, **restricted**, and **multiverse**.

---

### Post by rokkaman on 2007-10-13
> **por100pre1 said:**
> ```
gksudo software-properties-gtk
```

Check **main**, **universe**, **restricted**, and **multiverse**.

**Thank you so much!**

Thank you all for helping me out!

---

### Post by stanbryan81 on 2007-10-13
I was having the same problem and this worked. Thanks guys.

---

### Post by por100pre1 on 2007-10-13
Glad to help! Rokkaman and StanBryan81, welcome to the forums! :)

---

