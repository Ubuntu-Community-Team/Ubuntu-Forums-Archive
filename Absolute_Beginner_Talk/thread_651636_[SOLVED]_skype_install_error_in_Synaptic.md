---
title: "[SOLVED] skype install error in Synaptic"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by goldencj on 2007-12-27
skype:
  Depends: libasound2 (>1.0.12) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.5 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libqt4-core (>=4.2.1) but 4.1.2-1ubuntu1.1 is to be installed
  Depends: libqt4-gui (>=4.2.1) but 4.1.2-1ubuntu1.1 is to be installed
  Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed

what does this mean?

---

### Post by goldencj on 2007-12-27
How do I add these repositories and enable them?

So far I added libasound2,libc6,libgcc1,libqt4-core,ibqt4-gui,libstdc++6.

Didn't make a difference.  Is the ans. that I need to enable them and if so how?

---

### Post by wormser on 2007-12-27
System> Administration> Software Sources then check main, universe and multiverse.  Skype itself is in the medibuntu repository.  So we need to add it.

Ubuntu 7.10 "Gutsy Gibbon" other versions of Ubuntu [here]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then, add the GPG Key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get update
```

```
sudo apt-get install skype
```

That should work.  When you post error messages you need to put all the details in it, like what command caused them and what version of Ubuntu you are using.

---

### Post by goldencj on 2007-12-27
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is to be installed
         Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20.5 is to be installed
         Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
         Depends: libqt4-core (>= 4.2.1) but 4.1.2-1ubuntu1.1 is to be installed         Depends: libqt4-gui (>= 4.2.1) but 4.1.2-1ubuntu1.1 is to be installed
         Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installedE: Broken packages
tlc@tlc-desktop:~$

Did all that and got this...

---

### Post by wormser on 2007-12-27
What version of Ubuntu are you running and post the result of **uname -a**.

---

### Post by goldencj on 2007-12-27
If I'm using Ubuntu 6.06 perhaps upgrading 7.10 would help?

---

### Post by goldencj on 2007-12-27
tlc@tlc-desktop:~$ uname -a
Linux tlc-desktop 2.6.15-29-386 #1 PREEMPT Mon Sep 24 17:18:25 UTC 2007 i686 GNU/Linux
tlc@tlc-desktop:~$

---

### Post by goldencj on 2007-12-27
How do I properly thank you?

---

### Post by wormser on 2007-12-27
You should be fine with Dapper.  The medibuntu repository I posted was for Gusty.  You need to use the right repository for this to work.  First we need to remove the Gusty medibuntu repository.

System> Administration> Software Sources> Third-Party Software tab> highlight the medibuntu repositories and click the remove button at the bottom.  Next we will add the Dapper medibuntu repositories.

Ubuntu 6.06 "Dapper Drake":

```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then, add the GPG Key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get update
```
```
sudo apt-get install skype
```

If you are still having problems post your /etc/apt/sources.list file.

```
gedit /etc/apt/sources.list
```

---

### Post by goldencj on 2007-12-27
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

 still the same errors

---

### Post by wormser on 2007-12-27
> **goldencj said:**
> deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
[COLOR="Red"]**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main**[/COLOR]

 still the same errors

Remove the whole line in red because it is for Feisty.

```
sudo apt-get update
```
```
sudo apt-get install skype
```

If it still has problems go into Software Sources again and uncheck Backports on the Udates tab.  Then do the update and install commands again.

---

### Post by goldencj on 2007-12-28
There I installed Skype-static instead of Skype and it worked.

---

