---
title: "Questions on repositories!"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by lieobry on 2007-04-22
I would like to make some questions about repositories and generally how to install things:

First of all my **source.list** is this:> # 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main #Added by software-properties

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#Givre's repository (ntfs-3g & fuse 2.5.3)
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main
deb-src [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main

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

**1)** I have problem with my updates. I take a message like this: "Could not download all repository indexes ...." and then "...W: GPG error: [http://givre.cabspace.com](http://givre.cabspace.com) dapper Release: The following signatures were invalid: NODATA 1 NODATA 2" (I don't know where can I upload a screenshot)

**2) **Also I want to install an application from internet ([http://www.kde-apps.org/content/show.php/keeper?content=26178](http://www.kde-apps.org/content/show.php/keeper?content=26178)). I download a file tar.gz. I 've tried with command make (after I have installed build-essential) but I take this message "make: *** No targets specified and no makefile found.  Stop.
". Is there any way to add this site to my repositories so I can download from Synaptic.


Thanks in advance

---

### Post by adam_kimber on 2007-04-22
You will need to remove this Repository from your sources list. This repo is for dapper and can cause problems if you use it within Feisty. Package conflicts could occur etc.

```
#Givre's repository (ntfs-3g & fuse 2.5.3)
deb http://givre.cabspace.com/ubuntu/ dapper main
deb-src http://givre.cabspace.com/ubuntu/ dapper main
```

When searching in my Repos I find ntfs-3g      so that can be installed without the above repo. See my sources.list below. 

As for Keeper the downloaded package does not require compiling. Just run keeper.py. You can either do this by double clicking on keeper.py and then selecting run. Or from the terminal in the keeper directory typing the following. 

```
./keeper.py
```

----------------------
Sources.list

```
##### OFFICIAL REPOS #####

## Ubuntu
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Updates
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Security
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse


##### UNOFFICAL REPOS #####

## Universe and Multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ feisty free
deb http://medibuntu.sos-sts.com/repo/ feisty non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free
deb-src http://medibuntu.sos-sts.com/repo/ feisty non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## Fonts 
deb http://www.telemail.fi/mlind/ubuntu feisty fonts
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts

```

---

### Post by lieobry on 2007-04-22
The 1st problem has been solved (by deleting givre's repository)

I still don't know what to do with the applications from the internet and I also want to ask about these two groups of repositories:> ### PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#I don't know what is this
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free

### CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
#I don't know what is this
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

My update manager has found some updates on PLF Repo(for Amarok).


Thanks for your help!!

---

### Post by adam_kimber on 2007-04-22
The two Repositories listed are what I use for packages such as "DECSS" used to play DVDs. However in some countries the law states that use of such packages is illegal. Hence the note:
```
### PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
```
PLF stands for Penguin Liberation Front and their about page goes into more depth. [http://plf.zarb.org/about.php](http://plf.zarb.org/about.php)  

Ubuntu does not offer technical support on any of the packages within that repo. 

The one below is for commercial software, no source code is provided for these, just the program, they will also have differing license agreements. 

The program you linked to is a python program. Download it, extract it and then run it! No compiling required.

---

### Post by lieobry on 2007-04-22
I guess you are right about the keeper, but after I click run (or run in terminal) nothing happens. The prompt window(the one with run, tun in terminal, etc) leaves and there is nothing else happening!!

Thank really much for helping and informing me!!!!!!

Leonidas

---

### Post by adam_kimber on 2007-04-22
Yeah I found that problem too. Probably best to mail the author. If you run the program from the command line theeeen you might get some errors that might help the author of the program fix the problem.

---

### Post by lieobry on 2007-04-23
Thanks for your great help but now there is another problem!!!!!

I was trying to install wine (by adding a repository) annd when I was updating it couldn't connect to this repository. After a reboot I'm trying to update from update manager and I take this error message:> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


As you can imagine I need your help again!!!
Thanks in advance...

---

### Post by adam_kimber on 2007-04-23
Looks like you are running two processes that install files at once. Say Synaptic and update manager, or apt-get and aptitude. The last two are command line programs. 

Also are you running the update process as root? Does it ask for your password?

---

### Post by Pobega on 2007-04-23
Make sure you aren't running any other package managers, i.e. update-notifier/synaptic/apt/aptitude/dselect. Only one may be running at a time, to prevent configuration files becoming corrupted or wrong.

---

### Post by lieobry on 2007-04-23
Ok problem solved! I guess you were right Pobega!
Thank you all...

---

### Post by garbergs on 2007-04-29
> **adam_kimber said:**
> You will need to remove this Repository from your sources list. This repo is for dapper and can cause problems if you use it within Feisty. Package conflicts could occur etc.


Is it also the other way around, i.e. if you're running Dapper that Feisty repositories can cause problems? 

How can you find out which repositories work on your current dist?

---

### Post by adam_kimber on 2007-04-29
> **garbergs said:**
> Is it also the other way around, i.e. if you're running Dapper that Feisty repositories can cause problems? 

How can you find out which repositories work on your current dist?

Yes using Feisty repos on Dapper can cause problems. Using packages that are meant for another distribution is not recommended. 

So for instance using packages from another version let alone another Debian based distribution such as Xandros, MEPIS or even Debian itself can cause problems. This is due to dependencies being different. Such as package A under Ubuntu requires B and C but under Debian it requires B C and X, X might not be available in any of  your repositories, and adding more repos is not the answer. Hence the warning flag on using packages and repos from other versions and distributions. 

Most repos have a string in them that refers to the distribution that you are using such as 

```
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
```

The above has feisty in it therefore it will work on feisty but probably not any other. Some have Ubuntu as the string and those SHOULD work on all Ubuntu versions, but experience tells me it sometime doesn't. If it states anything other than an ubuntu version then it would be unwise to use such a repo. 

Hope this helps! :D

---

### Post by garbergs on 2007-04-29
Good explanation, Adam!
Thanks!

---

