---
title: "Error while installing amarok"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Eforce on 2007-12-06
The following packages have unmet dependencies:
  amarok: Depends: amarok-xine but it is not going to be installed
          Depends: kdelibs4c2a (>= 4:3.5.7-1) but 4:3.5.6-0ubuntu14.1 is to be installed
          Depends: libart-2.0-2 (>= 2.3.18) but 2.3.17-1 is to be installed
          Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
          Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.1 is to be installed
          Depends: libgcc1 (>= 1:4.2.1) but 1:4.1.2-0ubuntu4 is to be installed
          Depends: libglib2.0-0 (>= 2.14.0) but 2.12.11-0ubuntu1 is to be installed
          Depends: libgpod3 but it is not going to be installed
          Depends: libmtp6 but it is not installable
          Depends: libruby1.8 (>= 1.8.6.36) but 1.8.5-4ubuntu2 is to be installed
          Depends: libstdc++6 (>= 4.2.1) but 4.1.2-0ubuntu4 is to be installed
          Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
E: Broken packages

This is what I get when I try to use the $ apt-get install amarok
Any help?

Also I have an Ipod touch I transfered one song from Rythmbox player to my ipod and now my ipod says I dont have any music. Amarok should help right?

---

### Post by Hospadar on 2007-12-06
you might need to enable the universe and multiverse repos if you havn't done so already.  System->Administration->Software Sources.  If they are already enabled, what happens when you do ```
sudo apt-get install amarok-xine
```

---

### Post by Eforce on 2007-12-06
They are and still get the same error

---

### Post by Eforce on 2007-12-06
The following packages have unmet dependencies:
  amarok-xine: Depends: amarok (= 2:1.4.7-0ubuntu3+ppa1) but it is not going to be installed
               Depends: amarok but it is not going to be installed
               Depends: kdelibs4c2a (>= 4:3.5.7-1) but 4:3.5.6-0ubuntu14.1 is to be installed
               Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
               Depends: libgcc1 (>= 1:4.2.1) but 1:4.1.2-0ubuntu4 is to be installed
               Depends: libstdc++6 (>= 4.2.1) but 4.1.2-0ubuntu4 is to be installed
               Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
E: Broken packages

---

### Post by Eforce on 2007-12-06
Somebody?

---

### Post by dfreer on 2007-12-06
Have you tried using this command yet?
```
sudo apt-get -f install
```

What version of ubuntu are you running, and how did you try to install amarok (using a .deb from somewhere, or using apt-get)?

Also, if you can post the output of this command:
```
cat /etc/apt/sources.list
```

---

### Post by mahiyar on 2007-12-06
Try using the synaptic package manager to install something with such huge dependencies, it is better then the command line for novices in the sense it will suggest what additional packages to install.

---

### Post by FuturePilot on 2007-12-06
> **mahiyar said:**
> Try using the synaptic package manager to install something with such huge dependencies, it is better then the command line for novices in the sense it will suggest what additional packages to install.
Synaptic is just a front end to apt-get. When you install a package through Synaptic it actually executes apt-get install package. There's no difference between using Synaptic to install or using the command line to install.

---

### Post by mahiyar on 2007-12-06
What I meant is that the dialog in synaptic is easy to understand for novices.

---

### Post by Eforce on 2007-12-06
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END

I did try that command

I did it through apt get

---

### Post by FuturePilot on 2007-12-06
> **Eforce said:**
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

**deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main**

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END

I did try that command

I did it through apt get

Seems that that Gutsy repo in there is causing the problems.
Open the file as root with gedit
```
gksudo gedit /etc/apt/sources.list
```
 Place a # in front of the line that is in **Bold**
Then run
```
sudo apt-get update
```
Then try to install Amarok.

---

### Post by Eforce on 2007-12-06
I have Feisty

---

### Post by FuturePilot on 2007-12-06
> **Eforce said:**
> I have Feisty

But you have a repo for Gutsy in there.

---

### Post by Eforce on 2007-12-06
> **FuturePilot said:**
> Seems that that Gutsy repo in there is causing the problems.
Open the file as root with gedit
```
gksudo gedit /etc/apt/sources.list
```
 Place a # in front of the line that is in **Bold**
Then run
```
sudo apt-get update
```
Then try to install Amarok.

Thank you. I am installing it right now

---

### Post by FuturePilot on 2007-12-06
No problem :)

---

### Post by OldDog1 on 2007-12-07
Hi, I am trying to install Amarok as well. Here is what I get:

mfelkins@mfelkins-desktop:~$ sudo apt-get install amarok-xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok-xine
mfelkins@mfelkins-desktop:~$ 

So where do I get the pkg?

---

### Post by dfreer on 2007-12-07
Just try installing amarok normally:
```
sudo apt-get install amarok
```
If that gives you the same error, post the same information we have the OP post.

---

